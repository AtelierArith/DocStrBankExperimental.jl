```
XPRSinit(f, path)
```

Initialize Xpress, call function `f`, free Xpress. Xpress is freed no matter whether `f` fails, raises an exception ...

`f` : The function to execute.

`path` : Path to license, can be the empty string to look in default places.
