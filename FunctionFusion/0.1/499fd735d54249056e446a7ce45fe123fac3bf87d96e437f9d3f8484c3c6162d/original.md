```
visualize(what, [format]; parameters...)
```

Provides visualization in MIME `format` for `what`. `what` can be either provider or vector of providers If `format` is not specified then it is chosen automatically:

  * If `GrahpViz` package is not loaded then it is `MIME"text/vnd.graphviz"` which is a graphviz document.
  * If `GraphViz` package is loaded then it would be `MIME"image/svg+xml"` which is a .svg image.

Load GraphViz in your REPL to have visualization as picture (automatically displayed in VScode).

`parameters`:

  * `mod=Main` display names relative to that module
  * `depth=Inf` display only `depth` nesting of the graph
  * `hide_types=False` hide types of the artifacts
