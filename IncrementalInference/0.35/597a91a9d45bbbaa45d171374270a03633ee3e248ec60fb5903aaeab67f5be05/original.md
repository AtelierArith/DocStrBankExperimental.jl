```julia
drawTreeAsyncLoop(tree, opt; filepath, dotreedraw)

```

If opt.drawtree then start an async task to draw tree in a loop according to opt.drawtreerate.

Notes

  * wont draw if opt.drawtree=false, just skips back to caller.
  * Currently @async
  * use `opt.showtree::Bool`
  * Does not work too well when opt.async during solveTree! call, but user can use this function separately.

DevNotes

  * TODO, use Threads.@spawn instead.

Related

drawTree, drawGraph
