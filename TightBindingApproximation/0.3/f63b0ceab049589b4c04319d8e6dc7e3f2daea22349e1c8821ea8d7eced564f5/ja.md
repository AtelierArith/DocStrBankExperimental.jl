```
eigvals(tba::Union{TBA, Algorithm{<:TBA}}, k::Union{AbstractVector{<:Number}, Nothing}=nothing; options...) -> Vector{<:Number}
eigvals(tba::Union{TBA, Algorithm{<:TBA}}, reciprocalspace::ReciprocalSpace; options...) -> Vector{<:Vector{<:Number}}
```

自由量子格子系の固有値を取得します。
