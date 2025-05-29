```
tess_available_languages(
    inst::TessInst
)::Union{Vector{String}, Nothing}
```

利用可能な言語のリストを取得します。エラーが発生した場合は `nothing` を返します。

**引数:**

| T   | 名前   | デフォルト | 説明                  |
|:--- |:---- |:----- |:------------------- |
| R   | inst |       | 利用可能な言語を照会するインスタンス。 |

**詳細:**

`tess*init()` 関数で使用できる言語のリストを取得します。このメソッドは `tess*init()` が呼び出された後にのみ何かを返します。

**例:**

```jldoctest
julia> using Tesseract

julia> download_languages("eng+fra+spa")
true

julia> instance = TessInst("eng")
Allocated Tesseract instance.

julia> tess_available_languages(instance)
3-element Vector{String}:
 "eng"
 "fra"
 "spa"
```

関連情報: [`tess_init`](@ref), [`update_languages`](@ref), [`download_languages`](@ref)
