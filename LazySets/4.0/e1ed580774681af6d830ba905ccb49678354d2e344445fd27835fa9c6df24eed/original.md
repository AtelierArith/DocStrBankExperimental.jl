```
sample(X::LazySet{N}, num_samples::Int;
       [sampler]=_default_sampler(X),
       [rng]::AbstractRNG=GLOBAL_RNG,
       [seed]::Union{Int, Nothing}=nothing,
       [include_vertices]=false,
       [VN]=Vector{N}) where {N}
```

Random sampling of an arbitrary set `X`.

### Input

  * `X`           – set to be sampled
  * `num_samples` – number of random samples
  * `sampler`     – (optional, default: `_default_sampler(X)`) the sampler used;                  falls back to [`CombinedSampler`](@ref)
  * `rng`         – (optional, default: `GLOBAL_RNG`) random number generator
  * `seed`        – (optional, default: `nothing`) seed for reseeding
  * `include_vertices` – (optional, default: `false`) option to include the                  vertices of `X`
  * `VN`          – (optional, default: `Vector{N}`) vector type of the sampled                  points

### Output

A vector of `num_samples` vectors. If `num_samples` is not passed, the result is just one sample (not wrapped in a vector).

### Algorithm

See the documentation of the respective `Sampler`.

### Notes

If `include_vertices == true`, we include all vertices computed with `vertices`. Alternatively if a number $k$ is passed, we plot the first $k$ vertices returned by `vertices(X)`.
