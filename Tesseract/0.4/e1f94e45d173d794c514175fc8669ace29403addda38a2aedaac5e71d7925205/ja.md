```
tess_get_param(
    inst::TessInst,
    name::AbstractString,
    ::Type{String}
)::Union{String, Nothing}
```

TesseractエンジンからStringパラメータを取得します。値を取得できなかった場合は`nothing`を返します。

**引数:**

| T   | 名前              | デフォルト | 説明                     |
|:--- |:--------------- |:----- |:---------------------- |
| R   | inst            |       | 変数を読み取るインスタンス。         |
| R   | name            |       | 読み取るパラメータの名前。          |
| R   | ::Type{Float64} |       | Float64値を取得したいことを示します。 |

**例:**

```jldoctest
julia> using Tesseract

julia> download_languages()
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> tess_get_param(instance, "page_separator", String)
"\f"
```

関連情報: [`tess_params`](@ref), [`tess_params_parsed`](@ref), [`tess_set_param`](@ref)
