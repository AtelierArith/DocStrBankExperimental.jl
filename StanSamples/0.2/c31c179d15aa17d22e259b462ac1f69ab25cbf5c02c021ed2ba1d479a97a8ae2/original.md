```julia
read_samples(filename)

```

Read Stan samples from a CSV file or a `IO` stream.

Return a container of arrays, accessed by variables names as properties (eg like a `NamedTuple`, which is in fact the current implementation, but can possibly change). Each array has samples for a variable, with the last index varying for each draw.

```jldoctest
julia> io = IOBuffer("a,b.1,b.2,c.1.1,c.2.1,c.1.2,c.2.2
" *
                     "1.0,2.0,3.0,4.0,5.0,6.0,7.0
" *
                     "8.0,9.0,10.0,11.0,12.0,13.0,14.0");

julia> samples = read_samples(io);

julia> samples.a
2-element Array{Float64,1}:
 1.0
 8.0

julia> samples.b
2×2 ElasticArrays.ElasticArray{Float64,2,1}:
 2.0   9.0
 3.0  10.0

julia> samples.c
2×2×2 ElasticArrays.ElasticArray{Float64,3,2}:
[:, :, 1] =
 4.0  6.0
 5.0  7.0

[:, :, 2] =
 11.0  13.0
 12.0  14.0
```
