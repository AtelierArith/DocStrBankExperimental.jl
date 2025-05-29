```julia
buildTreeReset!(dfg; ...)
buildTreeReset!(
    dfg,
    eliminationOrder;
    ordering,
    drawpdf,
    show,
    filepath,
    viewerapp,
    imgs,
    ensureSolvable,
    eliminationConstraints
)

```

Build a completely new Bayes (Junction) tree, after first wiping clean all temporary state in fg from a possibly pre-existing tree.

DevNotes

  * replaces `resetBuildTreeFromOrder!`

Related:

buildTreeFromOrdering!, 
