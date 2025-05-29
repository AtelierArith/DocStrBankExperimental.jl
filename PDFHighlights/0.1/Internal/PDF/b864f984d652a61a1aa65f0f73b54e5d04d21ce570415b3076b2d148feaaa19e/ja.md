```
get_pages(
    target::String;
    concatenate::Bool=false
) -> Vector{Int32}
```

渡されたPDFまたは渡されたディレクトリ内で再帰的に見つかったすべてのPDFからページを抽出します。

# 引数

  * `target::String`: PDFファイルまたはPDFファイルが含まれるディレクトリ

# キーワード

  * `concatenate::Bool=false`: `true`の場合、ハイライトを連結します

# 戻り値

  * `Vector{Int32}`: ページ

# 例外

  * [`get_highlights_comments_pages`](@ref) からの例外

# 例

```jldoctest; output = false
using PDFHighlights

path_to_pdf_dir = joinpath(pathof(PDFHighlights) |> dirname |> dirname, "test", "pdf")
path_to_pdf = joinpath(path_to_pdf_dir, "TestPDF.pdf")

get_pages(path_to_pdf_dir) == get_pages(path_to_pdf) == Int32[1, 2, 3, 4, 5, 6, 7, 8, 9]

# output

true
```
