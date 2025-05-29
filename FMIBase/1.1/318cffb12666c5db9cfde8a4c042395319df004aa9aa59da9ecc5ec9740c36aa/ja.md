```
getNamesAndInitials(md::fmi2ModelDescription)
```

変数の辞書をそのイニシャルと共に返します。

# 引数

  * `md::fmi2ModelDescription`: ModelVariablesの静的情報を提供する構造体。

# 戻り値

  * `dict::Dict{String, Cuint}`: String型のキーとCuint型の値を持つハッシュテーブルを構築する辞書を返します。したがって、`md.modelVariables[i].name::String`、`md.modelVariables[i].inital::Union{fmi2Initial, Nothing}`を持つ辞書を返します。（1:length(md.modelVariables)の各iに対して(name, initial)のタプルを作成します）

他にも[`getInitial`](@ref)を参照してください。
