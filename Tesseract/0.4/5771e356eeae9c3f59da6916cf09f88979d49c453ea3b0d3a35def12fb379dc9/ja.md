```
tess_get_param(
    inst::TessInst,
    name::AbstractString,
    ::Type{Bool}
)::Union{Bool, Nothing}
```

Tesseractエンジンからブールパラメータを取得します。値を取得できなかった場合は`nothing`を返します。

**引数:**

| T   | 名前           | デフォルト | 説明                  |
|:--- |:------------ |:----- |:------------------- |
| R   | inst         |       | 変数を読み取るインスタンス。      |
| R   | name         |       | 読み取る変数の名前。          |
| R   | ::Type{Bool} |       | ブール値を要求していることを示します。 |

**例:**

```jldoctest
julia> using Tesseract

julia> download_languages()
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> tess_get_param(instance, "edges_debug", Bool)
false
```

関連情報: [`tess_params`](@ref), [`tess_params_parsed`](@ref), [`tess_set_param`](@ref)
