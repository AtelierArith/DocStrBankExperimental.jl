```
get_authors_titles(dir::String) -> Tuple{Vector{String}, Vector{String}}
```

指定されたディレクトリ内のすべてのPDFから著者とタイトルを再帰的に抽出します。

# 引数

  * `dir::String`: PDFファイルがあるディレクトリ

# 戻り値

  * `Tuple{Vector{String}, Vector{String}}`: 著者とタイトル

# 例外

  * [`DirectoryDoesNotExist`](@ref): 指定されたディレクトリが存在しません
  * [`get_author_title`](@ref) からの例外

# 例

```jldoctest; output = false
using PDFHighlights

path_to_pdf_dir = joinpath(pathof(PDFHighlights) |> dirname |> dirname, "test", "pdf")

get_authors_titles(path_to_pdf_dir) == (["Pavel Sobolev"], ["A dummy PDF for tests"])

# output

true
```
