```julia
transferUpdateSubGraph!(dest, src; ...)
transferUpdateSubGraph!(dest, src, syms; ...)
transferUpdateSubGraph!(
    dest,
    src,
    syms,
    logger;
    updatePPE,
    solveKey
)

```

Transfer contents of `src::AbstractDFG` variables `syms::Vector{Symbol}` to `dest::AbstractDFG`. Notes

  * Reads, `dest` := `src`, for all `syms`
