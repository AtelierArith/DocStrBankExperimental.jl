このパッケージは、tty I/O制御のためのPOSIX呼び出しへのインターフェースを提供します。

これらの呼び出しの完全な説明については、[termios(3)](http://man7.org/linux/man-pages/man3/termios.3.html)マニュアルページを参照してください。

**使用法**

例:

```
using TERMIOS
const T = TERMIOS
term_stdin = T.termios()
T.tcgetattr(stdin, term_stdin)
term_stdin.c_iflag |= T.IGNBRK
T.tcsetattr(stdin, T.TCSANOW, term_stdin)
```
