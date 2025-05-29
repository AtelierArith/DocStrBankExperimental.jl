```
weak_norm(B::Basis)
```

Return the type of the weak norm of the basis

# Example

```jldoctest
julia> using RigorousInvariantMeasures

julia> B = Ulam(1024)
Ulam{LinRange{Float64, Int64}}(LinRange{Float64}(0.0, 1.0, 1025))

julia> weak_norm(B)
L1
```
