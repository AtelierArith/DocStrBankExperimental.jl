This package provides an interface to the POSIX calls for tty I/O control.

For a complete description of these calls, see the [termios(3)](http://man7.org/linux/man-pages/man3/termios.3.html) manual page.

**Usage**

Example:

```
using TERMIOS
const T = TERMIOS
term_stdin = T.termios()
T.tcgetattr(stdin, term_stdin)
term_stdin.c_iflag |= T.IGNBRK
T.tcsetattr(stdin, T.TCSANOW, term_stdin)
```
