Kraus representation of a quantum channel

```jldoctest
julia> @op A₁; @op A₂; @op A₃;

julia> K = kraus(A₁, A₂, A₃)
𝒦(A₁,A₂,A₃)

julia> @op ρ;

julia> K*ρ
A₁ρA₁†+A₂ρA₂†+A₃ρA₃†
```
