```julia
makeCsmMovie(fg, tree; ...)
makeCsmMovie(
    fg,
    tree,
    cliqs;
    assignhist,
    show,
    filename,
    frames
)

```

Convenience function to assign and make video of CSM state machine for `cliqs`.

Notes

  * Probably several teething issues still (lower priority).
  * Use `assignhist` if solver params async was true, or errored.

Related

csmAnimate, printCliqHistorySummary
