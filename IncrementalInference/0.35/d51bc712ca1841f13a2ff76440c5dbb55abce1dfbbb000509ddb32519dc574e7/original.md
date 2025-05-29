```julia
setValKDE!(vd, pts, bws)
setValKDE!(vd, pts, bws, setinit)
setValKDE!(vd, pts, bws, setinit, ipc)

```

Set the point centers and bandwidth parameters of a variable node, also set `isInitialized=true` if `setinit::Bool=true` (as per default).

Notes

  * `initialized` is used for initial solve of factor graph where variables are not yet initialized.
  * `inferdim` is used to identify if the initialized was only partial.
