```
get_comments(target::String; concatenate::Bool=false) -> Vector{String}
```

渡されたPDFまたは渡されたディレクトリ内で再帰的に見つかったすべてのPDFからコメントを抽出します。

# 引数

  * `target::String`: PDFファイルまたはPDFファイルが含まれるディレクトリ

# キーワード

  * `concatenate::Bool=false`: `true`の場合、ハイライトを連結します

# 戻り値

  * `Vector{String}`: コメント

# 例外

  * [`get_highlights_comments_pages`](@ref) からの例外

# 例

```jldoctest; output = false
using PDFHighlights

path_to_pdf_dir = joinpath(pathof(PDFHighlights) |> dirname |> dirname, "test", "pdf")
path_to_pdf = joinpath(path_to_pdf_dir, "TestPDF.pdf")

get_comments(path_to_pdf_dir; concatenate=true) ==
get_comments(path_to_pdf; concatenate=true) ==
["Comment 1", "Comment 2 Comment 3", "Comment 4", "", "", "", ""]

# output

true
```
