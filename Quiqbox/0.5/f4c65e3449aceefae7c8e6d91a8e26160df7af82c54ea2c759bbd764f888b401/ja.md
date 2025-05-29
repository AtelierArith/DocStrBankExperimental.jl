```
eeInteractions(bs::Union{Tuple{Vararg{AbstractGTBasisFuncs{T, D}}}, 
                         AbstractVector{<:AbstractGTBasisFuncs{T, D}}}) -> 
Array{T, 4}
```

基底セットが与えられたときの電子-電子相互作用のテンソル（化学者の表記法）を返します。
