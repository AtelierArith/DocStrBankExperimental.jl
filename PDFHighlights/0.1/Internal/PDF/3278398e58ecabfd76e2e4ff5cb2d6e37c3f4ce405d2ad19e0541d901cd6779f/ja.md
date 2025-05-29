```
get_title(pdf::String) -> String
```

PDFからタイトルを抽出します。

# 引数

  * `pdf::String`: PDFファイルへの絶対パスまたは相対パス

# 戻り値

  * `String`: タイトル

# 例外

  * [`get_author_title`](@ref) からの例外

# 例

```jldoctest; output = false
using PDFHighlights

path_to_pdf = joinpath(
    pathof(PDFHighlights) |> dirname |> dirname,
    "test",
    "pdf",
    "TestPDF.pdf",
)

get_title(path_to_pdf) == "A dummy PDF for tests"

# output

true
```
