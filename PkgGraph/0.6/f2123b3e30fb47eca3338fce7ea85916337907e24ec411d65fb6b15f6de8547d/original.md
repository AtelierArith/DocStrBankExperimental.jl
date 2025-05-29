```
depgraph_image(
    pkgname;
    dir    = tempdir(),
    fmt    = :png,
    bg     = bg(fmt),
    open   = true,
    post   = true,
    kw...
)
```

Render the dependency graph of the given package as an image in `dir`, and open it with your default image viewer. Uses the external program '`dot`' (see [graphviz.org](https://graphviz.org)), which must be available on `PATH`.

`bg`: background colour for the image. Default is `:white` if `fmt = :png`, and `:transparent` otherwise.

`fmt` is an output file format supported by dot, such as `:svg` or `:png`.
If `fmt` is `:svg`, and `post` is `true` (default), the generated SVG file is post-processed, to add light and dark-mode CSS.

To only create the image, without automatically opening it, pass `open = false`.

Other keyword arguments are passed on to [`depgraph_as_dotstr`](@ref)
