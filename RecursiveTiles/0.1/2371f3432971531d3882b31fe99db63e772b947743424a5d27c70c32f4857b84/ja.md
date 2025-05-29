```
AbstractTile{P,T,U,S,N} <: AbstractVector{T}
```

タイル抽象のスーパークラスで、`P<:AbstractVector{T}` とインデックス `U<:Tuple{Vararg{S,N}}` を含む構造体です。
