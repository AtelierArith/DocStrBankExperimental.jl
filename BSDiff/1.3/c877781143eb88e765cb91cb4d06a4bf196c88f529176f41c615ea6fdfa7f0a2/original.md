```
bspatch(old, [ new, ] patch; format = [ :classic | :endsley ]) -> new
```

Apply a binary patch given by the `patch` argument to the content of `old` to produce the content of `new`. All arguments can be strings or IO handles. If no `new` argument is provided, the new data is written to a temporary file whose path is returned.

Note that the optional argument is the middle argument, which is a bit unusual but makes the argument order when passing all three paths consistent with the `bspatch` command and with the `bsdiff` function.

By default `bspatch` auto-detects the patch format, so the `format` keyword argument is usually unnecessary. If you wish to restrict the format of patch that will be accepted, however, you can use this keyword argument: `bspatch` will raise an error unless the patch file has indicated format.
