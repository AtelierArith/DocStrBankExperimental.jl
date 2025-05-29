```
tess_initialized_languages(
    inst::TessInst
)::Union{String, Nothing}
```

最後に初期化された言語を取得します。エラーがあった場合は `nothing` を返します。

**引数:**

| T   | 名前   | デフォルト | 説明             |
|:--- |:---- |:----- |:-------------- |
| R   | inst |       | 言語を取得するインスタンス。 |

**詳細:**

このメソッドは、最後の `tess_init()` 呼び出しで提供された言語文字列を返します。

**例:**

```jldoctest
julia> using Tesseract

julia> download_languages("eng+fra")
true

julia> instance = TessInst("eng+fra")
Allocated Tesseract instance.

julia> tess_initialized_languages(instance)
"eng+fra"
```

参照: [`tess_init`](@ref)
