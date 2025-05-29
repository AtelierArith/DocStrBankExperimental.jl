```
Lattice(𝐚::AbstractVector, 𝐛::AbstractVector, 𝐜::AbstractVector)
```

Construct a `Lattice` from three basis vectors.

# Examples

```jldoctest
julia> 𝐚, 𝐛, 𝐜 = [1.2, 2.3, 3.4], [4.5, 5.6, 6.7], [7.8, 8.9, 9.10];

julia> Lattice(𝐚, 𝐛, 𝐜)
Lattice{Float64}
 1.2  4.5  7.8
 2.3  5.6  8.9
 3.4  6.7  9.1
```
