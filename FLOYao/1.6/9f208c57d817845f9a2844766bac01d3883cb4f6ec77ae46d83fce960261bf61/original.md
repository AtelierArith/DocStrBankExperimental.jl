```
MajoranaSum{T}
MajoranaSum(terms::Vector{MajoranaTerm{T}})
MajoranaSum(terms::Dict{Vector{Int}, T})
MajoranaSum(op::AbstractBlock)
```

A sum of [`FLOYao.MajoranaTerm`](@ref)s to be used as a more performant replacement of `op::Yao.AbstractBlock` in [`expect`](@ref) and `expect'`

`Yao.AbstractBlock`s that are sums of (scaled) tensor products of Pauli gates can be directly converted to `MajoranaSum`s:

```jldoctest; setup=:(using FLOYao, Yao)
julia> yaoham = (put(4, 1=>Z) + 2kron(4, 1=>X, 2=>Z, 3=>Z, 4=>X) + 3.5put(4, 2=>Z)
                 + 0.5kron(4, 1=>Z, 2=>Z) - kron(4, 2 => X, 4 => Y));

julia> MajoranaSum(yaoham)
5-element MajoranaSum{ComplexF64}:
  [4, 5, 6, 8] : -1.0 - 0.0im
  [2, 7] : 0.0 + 2.0im
  [1, 2, 3, 4] : -0.5 - 0.0im
  [1, 2] : 0.0 - 1.0im
  [3, 4] : 0.0 - 3.5im
```
