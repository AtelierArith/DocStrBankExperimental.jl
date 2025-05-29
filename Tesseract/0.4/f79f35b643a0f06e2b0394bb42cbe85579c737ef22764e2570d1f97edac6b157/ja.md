```
download_languages(
    languages::AbstractString = "eng";
    target::AbstractString = "tessdata",
    baseUrl::AbstractString = DATA_URL,
    force::Bool = false
)::Bool
```

指定された言語のデータファイルをダウンロードします。ファイルのダウンロードに問題がある場合は`false`を返します。

**引数:**

| T   | 名前        | デフォルト      | 説明                        |
|:--- |:--------- |:---------- |:------------------------- |
| O   | languages | `eng`      | ダウンロードする言語を"+"で区切って指定します。 |
| K   | target    | `tessdata` | データファイルを保存するディレクトリ。       |
| K   | baseUrl   | ...        | ファイルをダウンロードするためのベースURL。   |
| K   | force     | `false`    | ファイルが存在していてもダウンロードするべきか？  |

**詳細:**

デフォルトでは、データファイルは現在のディレクトリの下にある「tessdata」ディレクトリに保存され、ファイルはhttps://github.com/tesseract-ocr/tessdata_bestからダウンロードされます。

通常、ファイルがすでにダウンロードされている場合は再度ダウンロードされません。ただし、`force`がtrueの場合は、ファイルがダウンロードされ、既存のファイルが上書きされます。

関連情報: [`update_languages`](@ref)
