```
KernelSizeAligned(Δsize; pad)
KernelSizeAligned(Δs::Integer...;pad)
```

Strategy for changing kernel size of convolutional layers where filters remain phase aligned. In other words, the same  element indices are removed/added for all filters and only 'outer' elements are dropped or added.

Call with vertex as input to change weights.

### Examples

```jldoctest
julia> using NaiveNASflux, Flux

julia> cv = fluxvertex(Conv((3,3), 1=>1;pad=SamePad()), conv2dinputvertex("in", 1));

julia> cv(ones(Float32, 4,4,1,1)) |> size
(4, 4, 1, 1)

julia> layer(cv).weight |> size
(3, 3, 1, 1)

julia> cv |> KernelSizeAligned(-1, 1; pad=SamePad());

julia> cv(ones(Float32, 4,4,1,1)) |> size
(4, 4, 1, 1)

julia> layer(cv).weight |> size
(2, 4, 1, 1)
```
