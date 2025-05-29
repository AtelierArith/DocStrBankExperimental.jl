```
outputtype(m::AbstractModel)
```

モデルを `apply` したときに得られる出力のスーパタイプを返します。結果はモデルがオープンかクローズかによって異なります：

```
outputtype(M::AbstractModel{O}) = isopen(M) ? Union{Nothing,O} : O
```

モデルがクローズの場合、`outputtype(m)` は `outcometype(m)` と等しいことに注意してください。

参照： [`isopen`](@ref), [`apply`](@ref), [`outcometype`](@ref), [`AbstractModel`](@ref).
