```
nugap(G; map = map)
```

Compute the νgap between the nominal system `Gₙ` represented by the first particle index in `G`, and all other systems in `G`. Returns a `Particles` object with the νgap for each system in `G`.

See `with_nominal` to endow uncertain values with a nominal value, and `nominal` to extract the nominal value.

The value returned by this function, `νᵧ` is useful for robust synthesis, by designing a controller for the nominal system `Gₙ`, that achieves an [`ncfmargin`](@ref) of at least `νᵧ` is guaranteed to stabilize all realizations within `G`. 

To speed up computation for large systems, a threaded or distributed `map` function can be supplied, e.g., `ThreadTools.tmap` or `Distributed.pmap`.
