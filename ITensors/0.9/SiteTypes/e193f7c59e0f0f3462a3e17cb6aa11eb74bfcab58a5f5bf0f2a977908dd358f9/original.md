```
op(X::AbstractArray, s::Index...)
op(M::Matrix, s::Index...)
```

Given a matrix M and a set of indices s,t,... return an operator ITensor with matrix elements given by M and indices s, s', t, t'

# Example

```julia
julia> s = siteind("S=1/2")
(dim=2|id=575|"S=1/2,Site")

julia> Sz = op([1/2 0; 0 -1/2],s)
ITensor ord=2 (dim=2|id=575|"S=1/2,Site")' (dim=2|id=575|"S=1/2,Site")
NDTensors.Dense{Float64, Vector{Float64}}

julia> @show Sz
Sz = ITensor ord=2
Dim 1: (dim=2|id=575|"S=1/2,Site")'
Dim 2: (dim=2|id=575|"S=1/2,Site")
NDTensors.Dense{Float64, Vector{Float64}}
 2×2
 0.5   0.0
 0.0  -0.5
ITensor ord=2 (dim=2|id=575|"S=1/2,Site")' (dim=2|id=575|"S=1/2,Site")
NDTensors.Dense{Float64, Vector{Float64}}
```
