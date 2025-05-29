```
deploy(project::Project, out, formats...; clean)
```

Build a Publish project from the given "virtual" `project` object.  Output is built in `out` directory, which is either an absolute path or relative to the present working directory. `formats` is the list of formats to build in `out`: `pdf` and `html` are supported.

# Keywords

  * `clean = false` controls whether to only include the final document in the provided `out` folder. This is only support for `formats` that are *all* classified as 'standalone' (`pdf` is currently the only such format).
