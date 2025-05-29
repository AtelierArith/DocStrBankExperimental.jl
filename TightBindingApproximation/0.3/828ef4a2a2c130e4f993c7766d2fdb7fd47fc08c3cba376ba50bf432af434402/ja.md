```
eigvecs(tba::Union{TBA, Algorithm{<:TBA}}, k::Union{AbstractVector{<:Number}, Nothing}=nothing; options...) -> Matrix{<:Number}
eigvecs(tba::Union{TBA, Algorithm{<:TBA}}, reciprocalspace::ReciprocalSpace; options...) -> Vector{<:Matrix{<:Number}}
```

自由量子格子系の固有ベクトルを取得します。
