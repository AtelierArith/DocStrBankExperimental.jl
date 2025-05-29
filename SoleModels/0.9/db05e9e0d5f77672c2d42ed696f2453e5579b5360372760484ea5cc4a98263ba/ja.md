```
outputtype(m::AbstractModel)
```

モデルを `apply` したときに得られる出力のスーパタイプを返します。

# 実装

結果は、モデルが不完全か完全かによって異なります。

```julia-repl
julia> outputtype(m::AbstractModel{O}) where {O} = iscomplete(m) ? O : Union{Nothing,O}
```

モデルが完全である場合、`outputtype(m)` は `outcometype(m)` と等しいことに注意してください。

関連情報として [`AbstractModel`](@ref), [`apply`](@ref), [`iscomplete`](@ref), [`outcometype`](@ref) を参照してください。
