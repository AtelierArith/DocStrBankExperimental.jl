```
get_highlights_comments_pages(
    target::String;
    concatenate::Bool=true
) -> Tuple{Vector{String}, Vector{String}, Vector{Int32}}
```

渡されたPDFまたは渡されたディレクトリ内で再帰的に見つかったすべてのPDFからハイライト、コメント、およびページを抽出します。

# 引数

  * `target::String`: PDFファイルまたはPDFファイルが含まれるディレクトリ

# キーワード

  * `concatenate::Bool=true`: `true`の場合、ハイライトを連結します

# 戻り値

  * `Tuple{Vector{String}, Vector{String}, Vector{Int32}}`: ハイライト、コメント、およびページ

# 例外

  * [`DoesNotExist`](@ref): 指定されたファイルまたはディレクトリが存在しません
  * [`NotPDF`](@ref): 指定されたパスが`.pdf`で終わっていません

# 例

```jldoctest; output = false
using PDFHighlights

path_to_pdf_dir = joinpath(pathof(PDFHighlights) |> dirname |> dirname, "test", "pdf")
path_to_pdf = joinpath(path_to_pdf_dir, "TestPDF.pdf")

get_highlights_comments_pages(path_to_pdf_dir) ==
get_highlights_comments_pages(path_to_pdf) ==
(
    [
        "Highlight 1",
        "Highlight 2 Highlight 3",
        "Highlight 4",
        "Highhighlight 5",
        "6th Highhigh light-",
        "High light 7",
        "8th Highlight-",
    ],
    ["Comment 1", "Comment 2 Comment 3", "Comment 4", "", "", "", ""],
    Int32[1, 2, 4, 6, 7, 8, 9],
)

# output

true
```
