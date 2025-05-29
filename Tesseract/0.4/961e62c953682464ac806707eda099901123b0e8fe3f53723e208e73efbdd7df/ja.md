```
tess_loaded_languages(
    inst::TessInst
)::Union{Vector{String}, Nothing}
```

OCRエンジンにロードされた言語のリストを取得します。エラーが発生した場合は`nothing`を返します。

**引数:**

| T   | 名前   | デフォルト | 説明             |
|:--- |:---- |:----- |:-------------- |
| R   | inst |       | 言語を取得するインスタンス。 |

**詳細:**

このメソッドは、Tesseractエンジンにロードされた言語を返します。一部の言語ファイルは追加の言語をロードします。`tess_initialized_languages()`とは異なり、このメソッドはクライアントによってロードするように指示された言語だけでなく、すべてのロードされた言語を返します。

**例:**

```jldoctest
julia> using Tesseract

julia> download_languages("eng+spa")
true

julia> instance = TessInst("eng+spa")
Allocated Tesseract instance.

julia> tess_loaded_languages(instance)
2-element Vector{String}:
 "eng"
 "spa"
```

関連情報: [`tess_init`](@ref)
