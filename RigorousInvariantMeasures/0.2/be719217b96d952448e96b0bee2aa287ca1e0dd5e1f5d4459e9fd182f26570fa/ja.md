```
is_refinement(Bfine::Basis, Bcoarse::Basis)
```

BfineがBcoarseの細分化であるかを確認します

# 例

```jldoctest
julia> using RigorousInvariantMeasures

julia> B = Ulam(1024)
Ulam{LinRange{Float64, Int64}}(LinRange{Float64}(0.0, 1.0, 1025))

julia> Bfine = Ulam(2048)
Ulam{LinRange{Float64, Int64}}(LinRange{Float64}(0.0, 1.0, 2049))

julia> is_refinement(Bfine, B)
true

julia> Bfine = Ulam(2049)
Ulam{LinRange{Float64, Int64}}(LinRange{Float64}(0.0, 1.0, 2050))

julia> is_refinement(Bfine, B)
false
```
