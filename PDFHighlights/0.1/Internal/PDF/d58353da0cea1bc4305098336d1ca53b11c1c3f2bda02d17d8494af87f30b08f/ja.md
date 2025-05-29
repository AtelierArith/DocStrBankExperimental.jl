```
get_author_title(pdf::String) -> Tuple{String, String}
```

PDFから著者とタイトルを抽出します。

# 引数

  * `pdf::String`: PDFファイルへの絶対パスまたは相対パス

# 戻り値

  * `Tuple{String, String}`: 著者とタイトル

# 例外

  * [`FileDoesNotExist`](@ref): 指定されたファイルが存在しません
  * [`NotPDF`](@ref): 指定されたパスが`.pdf`で終わっていません

# 例

```jldoctest; output = false
using PDFHighlights

path_to_pdf = joinpath(
    pathof(PDFHighlights) |> dirname |> dirname,
    "test",
    "pdf",
    "TestPDF.pdf",
)

get_author_title(path_to_pdf) == ("Pavel Sobolev", "A dummy PDF for tests")

# output

true
```
