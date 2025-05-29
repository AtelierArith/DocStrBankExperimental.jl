```
struct TessParam{T}
    name::String
    default::T
    desc::String
    debug::Bool
end
```

パラメータのデフォルト値に関する詳細を保持します。

**値:**

| 名前      | 説明                   |
|:------- |:-------------------- |
| name    | パラメータの名前/ID。         |
| default | パラメータのデフォルト値。        |
| desc    | 変数の説明。               |
| debug   | 値がデバッグパラメータであればTrue。 |

**詳細:**

この構造体は現在3つのフレーバーがあり、Tはデフォルト値に基づいてFloat64、Int32、またはStringのいずれかになります。

参照: [`tess_params_parsed`](@ref), [`tess_get_param`](@ref), [`tess_set_param`](@ref)
