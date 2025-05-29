```
flavors(::Type{<:AbstractProblem}) -> UnitRange
flavors(::GT) where GT<:AbstractProblem -> UnitRange
```

自由度のフレーバー（ドメイン）として整数のベクターを返します。

!!! warning
    フレーバーは `0:num_flavors-1` として定義されています。以前のバージョンのフレーバーにアクセスするには、[`flavor_names`](@ref) を使用してください。

