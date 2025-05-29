```julia
VortexFilament(Γ, v; ...)
VortexFilament(Γ, v, boundidx; isclosed)

```

Constructs a `VortexFilament` with strength `Γ` and vertices `v`. `boundidx` can be used to provide the indices of vertices that are considered as 'bound'. The constructor then set `freeidx` of the `VortexFilament` as the complementary list of indices. If the keyword `isclosed` is `true`, the `segments` of the `VortexFilament` will contain a segment that connects the first and last vertex in `v`, provided that these do not contain an infinite coordinate.
