```
eigen(tba::Union{TBA, Algorithm{<:TBA}}, k::Union{AbstractVector{<:Number}, Nothing}=nothing; options...) -> Eigen
eigen(tba::Union{TBA, Algorithm{<:TBA}}, reciprocalspace::ReciprocalSpace; options...) -> Tuple{Vector{<:Vector{<:Number}}, Vector{<:Matrix{<:Number}}}
```

自由量子格子系の固有値と固有ベクトルを取得します。
