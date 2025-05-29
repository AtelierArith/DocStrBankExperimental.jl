```
getInputNamesAndStarts(md::fmi2ModelDescription)
```

入力変数とその開始値の辞書を返します。

# 引数

  * `md::fmi2ModelDescription`: モデル変数の静的情報を提供する構造体。

# 戻り値

  * `dict::Dict{String, Array{fmi2ValueReferenceFormat}}`: キーがString型、値がfmi2ValueReferenceFormat型のハッシュテーブルを構築する辞書を返します。したがって、`(md.modelVariables[i].name::String, starts:: Array{fmi2ValueReferenceFormat})`を持つ辞書を返します。（inputIndicesの各iに対してタプル(name, starts)を作成します）

他にも[`getStartValue`](@ref)を参照してください。
