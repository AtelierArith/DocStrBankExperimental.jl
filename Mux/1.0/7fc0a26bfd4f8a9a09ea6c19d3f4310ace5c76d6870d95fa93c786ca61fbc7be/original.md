```
files(root, dirs=true)
```

Middleware to serve files in the directory specified by the absolute path `root`.

`req[:path]` will be combined with `root` to yield a filepath. If the filepath is contained within `root` (after normalisation) and refers to an existing file (or directory if `dirs=true`), then respond with the file (or a directory listing), otherwise call the next middleware.

If you'd like to specify a `root` relative to your current working directory or to the directory containing the file that your server is defined in, then you can use `pwd()` or `@__DIR__`, and (if you need them) `joinpath` or `normpath`.

# Examples

```
files(pwd()) # serve files from the current working directory
files(@__DIR__) # serve files from the directory the script is in

# serve files from the assets directory in the same directory the script is in:
files(joinpath(@__DIR__, "assets"))

# serve files from the assets directory in the directory above the directory the script is in:
files(normpath(@__DIR__, "../assets))
```
