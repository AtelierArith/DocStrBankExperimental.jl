```
get_comments_pages(
    target::String;
    concatenate::Bool=false,
) -> Tuple{Vector{String}, Vector{Int32}}
```

渡されたPDFまたは渡されたディレクトリ内で再帰的に見つかったすべてのPDFからコメントとページを抽出します。

# 引数

  * `target::String`: PDFファイルまたはPDFファイルが含まれるディレクトリ

# キーワード

  * `concatenate::Bool=false`: `true`の場合、ハイライトを連結します

# 戻り値

  * `Tuple{Vector{String}, Vector{Int32}}`: コメントとページ

# 例外

  * [`get_highlights_comments_pages`](@ref) からの例外

# 例

```jldoctest; output = false
using PDFHighlights

path_to_pdf_dir = joinpath(pathof(PDFHighlights) |> dirname |> dirname, "test", "pdf")
path_to_pdf = joinpath(path_to_pdf_dir, "TestPDF.pdf")

get_comments_pages(path_to_pdf_dir; concatenate=true) ==
get_comments_pages(path_to_pdf; concatenate=true) ==
(
    String["Comment 1", "Comment 2 Comment 3", "Comment 4", "", "", "", ""],
    Int32[1, 2, 4, 6, 7, 8, 9],
)

# output

true
```
