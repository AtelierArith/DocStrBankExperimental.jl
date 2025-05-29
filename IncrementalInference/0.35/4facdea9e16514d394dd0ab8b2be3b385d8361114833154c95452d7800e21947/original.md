```julia
drawGraph(fgl; viewerapp, filepath, engine, show)

```

Draw and show the factor graph `<:AbstractDFG` via system graphviz and xdot app.

Notes

  * Requires system install on Linux of `sudo apt-get install xdot`
  * Should not be calling outside programs.
  * Need long term solution
  * DFG's `toDotFile` a better solution – view with `xdot` application.
  * also try `engine={"sfdp","fdp","dot","twopi","circo","neato"}`

Notes:

  * Calls external system application `xdot` to read the `.dot` file format

      * ```toDot(fg,file=...); @async run(`xdot file.dot`)```

Related

drawGraphCliq, [`drawTree`](@ref), printCliqSummary, spyCliqMat
