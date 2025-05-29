```
NoOnset <: AbstractOnset
```

ユーザーが連続するイベント間に重複がないエポックデータをシミュレートしたい場合のケース。

# 例

```julia-repl
julia> onset_distribution = NoOnset()
NoOnset()
```

参照: [`UniformOnset`](@ref), [`LogNormalOnset`](@ref).
