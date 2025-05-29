```
render_asymptote(filename; render=4, format="png", ...)
```

render an exported asymptote file specified in the `filename`, which can also be given as a relative or full path

# Input

  * `filename`    filename of the exported `asy` and rendered image

# Keyword arguments

the default values are given in brackets

  * `render`:      (`4`) render level of asymptote passed to its `-render` option.  This can be removed from the command by setting it to `nothing`.
  * `format`:      (`"png"`) final rendered format passed to the `-f` option
  * `export_file`: (the filename with format as ending) specify the export filename
