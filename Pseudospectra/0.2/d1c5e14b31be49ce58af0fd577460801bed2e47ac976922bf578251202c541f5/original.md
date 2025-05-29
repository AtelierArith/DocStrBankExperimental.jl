```
driver!(ps_data, opts, gs=defaultgs(); revise_method=false)
```

Compute pseudospectra and plot a spectral portrait.

If using an iterative method to get some eigenvalues and a projection, invokes that first.

# Arguments

  * `ps_data::PSAStruct`: ingested matrix, as processed by `new_matrix`
  * `gs::GUIState`: object handling graphical output
  * `opts::Dict{Symbol,Any}`:

      * `:ax`, axis limits (overrides value stored in `ps_data`).
      * other options passed to `redrawcontour`, `arnoldiplotter!`

Note that many options stored in `ps_data` by `new_matrix()` influence the processing.

When revising a spectral portrait (`revise_method==true`), the following entries in `opts` also apply:

  * `:arpack_opts::ArpackOptions`,
  * `:direct::Bool`.
