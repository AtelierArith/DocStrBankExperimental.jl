```
tess_init(
    inst::TessInst,
    languages::AbstractString = "eng",
    dataPath::AbstractString = "tessdata"
)::Bool
```

指定された言語のインスタンスを初期化します。エラーが発生した場合は `false` を返します。

**引数:**

| T   | 名前        | デフォルト      | 説明               |
|:--- |:--------- |:---------- |:---------------- |
| R   | inst      |            | 初期化するインスタンス。     |
| O   | languages | `eng`      | 読み込む言語。          |
| O   | dataPath  | `tessdata` | 言語ファイルを探すディレクトリ。 |

**詳細:**

このメソッドは、OCR用の言語を再初期化するために複数回呼び出すことができます。複数の言語はプラスで区切って指定できます。英語とスペイン語を指定したい場合は "eng+spa" と指定できます。言語コードは（通常）[ISO 639-3](https://en.wikipedia.org/wiki/ISO_639-3) コードです。

注意: 言語ファイルは自動的にはダウンロードされません。別の手段でインストールしていない場合は、https://github.com/tesseract-ocr/tessdata_best からダウンロードできます。

**例:**

```jldoctest
julia> using Tesseract

julia> download_languages("eng+spa")
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> tess_init(instance, "spa")
true
```

参照: [`TessInst()`](@ref)
