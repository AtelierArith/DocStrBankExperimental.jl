```
tess_set_debug_param(
    inst::TessInst,
    name::AbstractString,
    value::Float64
)::Bool
```

Tesseractエンジンにデバッグ`Float64`変数を設定します。パラメータが見つからなかった場合は`false`を返します。

**引数:**

| T   | 名前    | デフォルト | 説明            |
|:--- |:----- |:----- |:------------- |
| R   | inst  |       | 変数を設定するインスタンス |
| R   | name  |       | 設定する変数の名前     |
| R   | value |       | 設定する値         |

**詳細:**

このメソッドは将来の拡張のために実装されています。現在、tesseractのデバッグパラメータはありません。

参照: [`tess_params`](@ref), [`tess_params_parsed`](@ref), [`tess_get_param`](@ref)
