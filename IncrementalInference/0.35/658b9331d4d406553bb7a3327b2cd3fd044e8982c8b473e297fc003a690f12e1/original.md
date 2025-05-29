```julia
drawTree(
    treel;
    show,
    suffix,
    filepath,
    xlabels,
    dpi,
    viewerapp,
    imgs
)

```

Draw the Bayes (Junction) tree by means of graphviz `.dot` files.  Ensure Linux packages  are installed `sudo apt-get install graphviz xdot`.

Notes

  * `xlabels` is optional `cliqid=>xlabel`.
