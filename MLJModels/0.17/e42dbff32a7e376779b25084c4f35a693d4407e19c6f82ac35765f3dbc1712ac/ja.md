```
localmodels(; modl=Main, wrappers=false)
localmodels(filters...; modl=Main, wrappers=false)
localmodels(needle::Union{AbstractString,Regex}; modl=Main, wrappers=false)
```

ユーザーがモジュール `modl` から現在利用可能なすべてのモデルをリストし、指定されたフィルターを通過する追加のモデルをリストします。ここでの *フィルター* は、モデルに対する `Bool` 値の関数です。

`load_path` を使用して、返されたモデルのいくつかのパスを取得します。以下の例のように：

```
ms = localmodels()
model = ms[1]
load_path(model)
```

[`models`](@ref) や [`load_path`](@ref) も参照してください。
