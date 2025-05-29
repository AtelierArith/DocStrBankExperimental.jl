```
path = localpath(title, checkfun, isfolder=false)
```

Get the path to a local file or folder (if isfolder is true), and ask the user if they haven't given it before. checkfun(path) is run, and only returns the path if true.
