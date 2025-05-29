```
getNamesAndDescriptions(md::fmi2ModelDescription)
```

変数とその説明の辞書を返します。

# 引数

  * `md::fmi2ModelDescription`: ModelVariablesの静的情報を提供する構造体。

# 戻り値

  * `dict::Dict{String, String}`: キーの型がString、値の型がStringのハッシュテーブルを構築する辞書を返します。したがって、`md.modelVariables[i].name::String`、`md.modelVariables[i].description::Union{String, Nothing}`を持つ辞書を返します。（1:length(md.modelVariables)の各iに対して(name, description)のタプルを作成します）
