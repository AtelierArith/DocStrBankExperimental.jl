```
qstop()
```

close everything and detach from qwtw library.

It maybe useful for debugging. What it does actually, it sends a command to the QT process to exit.
Have to call `qstart()` before, though.
