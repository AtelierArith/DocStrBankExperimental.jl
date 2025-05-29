```
tess_get_param(
    inst::TessInst,
    name::AbstractString,
    ::Type{T}
)::Union{T, Nothing} where T<:Integer
```

Tesseractエンジンから整数パラメータを取得します。値を取得できなかった場合は`nothing`を返します。

**引数:**

| T   | 名前        | デフォルト | 説明                |
|:--- |:--------- |:----- |:----------------- |
| R   | inst      |       | パラメータを読み取るインスタンス。 |
| R   | name      |       | 読み取るパラメータの名前。     |
| R   | ::Type{T} |       | 返す型。              |

**例:**

```jldoctest
julia> using Tesseract

julia> download_languages()
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> tess_get_param(instance, "edges_min_nonhole", Int)
12
```

関連情報: [`tess_params`](@ref), [`tess_params_parsed`](@ref), [`tess_set_param`](@ref)
