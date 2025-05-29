```julia
productbelief(
    denspts,
    manifold,
    dens,
    N;
    asPartial,
    dbg,
    logger
)

```

Take product of `dens` (including optional partials beliefs) as proposals to be multiplied together.

## Notes

  * Return points of full dimension, even if only partial dimensions in proposals.

      * 'Other' dimensions left unchanged from incoming `denspts`
  * `d` dimensional product approximation
  * Incorporate ApproxManifoldProducts to process variables in individual batches.

DevNotes

  * TODO Consolidate with [`AMP.manifoldProduct`](@ref), especially concerning partials.
