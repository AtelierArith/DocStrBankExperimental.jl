```
resolve("name/path", @__FILE__)
```

Is the function that lives directly behind the `datadep"name/path"` macro. If you are working the the names of the datadeps programmatically, and don't want to download them by mistake; it can be easier to work with this function.

Note though that you must include `@__FILE__` as the second argument, as DataDeps.jl uses this to allow reading the package specific `deps/data` directory. Advanced usage could specify a different file or `nothing`, but at that point you are on your own.
