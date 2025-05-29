```
XPRScreateprob(f, path)
```

Create an `XPRSprob` instance, execute `f`, and release the `XPRSprob` instance. The instance is released even if `f` exits with an error.

`f` : The function to execute

`path` : If this is not `nothing` then the function initializes Xpress (see `XPRSinit`)   with that path before creating the `XPRSprob` instance. When the `XPRSprob`   instance is destroyed, Xpress will be freed.
