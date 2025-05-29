```
TessInst(
    languages::AbstractString = "eng",
    dataPath::AbstractString = TESS_DATA
)
```

TessInstオブジェクトを初期化します。

**引数:**

| T   | 名前        | デフォルト      | 説明               |
|:--- |:--------- |:---------- |:---------------- |
| O   | languages | `eng`      | 読み込む言語。          |
| O   | dataPath  | `tessdata` | 言語ファイルを探すディレクトリ。 |

**詳細:**

このインスタンスによって識別される言語を変更するには、`tess_init()`を呼び出すことができます。複数の言語はプラスで区切って指定できます。したがって、英語とスペイン語を指定したい場合は「eng+spa」と指定できます。言語コードは（通常）[ISO 639-3](https://en.wikipedia.org/wiki/ISO_639-3)コードです。

**例:**

```jldoctest
julia> using Tesseract

julia> download_languages("eng+fra")
true

julia> instance = TessInst("eng+fra")
Allocated Tesseract instance.
```

参照: [`tess_init`](@ref).
