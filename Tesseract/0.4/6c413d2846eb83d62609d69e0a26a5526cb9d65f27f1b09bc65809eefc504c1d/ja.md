```
tess_set_debug_param(
    inst::TessInst,
    name::AbstractString,
    value::AbstractString
)::Bool
```

Tesseractエンジン内のデバッグ文字列変数を設定します。パラメータが見つからなかった場合は`false`を返します。

**引数:**

| T   | 名前    | デフォルト | 説明            |
|:--- |:----- |:----- |:------------- |
| R   | inst  |       | 変数を設定するインスタンス |
| R   | name  |       | 設定する変数の名前     |
| R   | value |       | 設定する値         |

**詳細:**

パラメータがデバッグ設定でない場合、値は変更されません。

**例:**

```jldoctest
julia> using Tesseract

julia> download_languages()
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> tess_set_debug_param(instance, "debug_file", "debug.log")
true
```

関連情報: [`tess_params`](@ref), [`tess_params_parsed`](@ref), [`tess_get_param`](@ref)
