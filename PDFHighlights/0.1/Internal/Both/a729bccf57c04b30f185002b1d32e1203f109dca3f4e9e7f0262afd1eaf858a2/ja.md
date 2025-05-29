```
get_highlights(target::String; concatenate::Bool=true) -> Vector{String}
```

CSVファイルが渡された場合は`Highlights`列から値を取得し、PDFファイルが渡された場合はそのハイライトを取得し、ディレクトリが渡された場合は再帰的に見つかったすべてのPDFからハイライトを取得します。

# 引数

  * `target::String`: CSVファイル、またはPDFファイル、またはPDFファイルを含むディレクトリ

# キーワード

  * `concatenate::Bool=true`: `true`の場合、ハイライトを連結します（PDFのみ）

# 戻り値

  * `Vector{String}`: ハイライト

# 例外

  * [`NotCSVorPDForDir`](@ref): 指定されたパスは`.csv`または`.pdf`で終わらず、ディレクトリでもありません
  * 例外: [`_get_highlights_from_CSV`](@ref)、[`_get_highlights_from_PDF`](@ref)から

# 例

```jldoctest; output = false
using PDFHighlights
HEADER = PDFHighlights.Internal.Constants.HEADER

path_to_pdf_dir = joinpath(pathof(PDFHighlights) |> dirname |> dirname, "test", "pdf")
path_to_pdf = joinpath(path_to_pdf_dir, "TestPDF.pdf")

(get_highlights(path_to_pdf_dir) == get_highlights(path_to_pdf) == String[
    "Highlight 1",
    "Highlight 2 Highlight 3",
    "Highlight 4",
    "Highhighlight 5",
    "6th Highhigh light-",
    "High light 7",
    "8th Highlight-",
]) |> println

_file, io = mktemp()
println(io, HEADER, '\n', "The world didn't stop spinning,,,,1")
flush(io)
file = _file * ".csv"
mv(_file, file)

get_highlights(file) == ["The world didn't stop spinning"]

# output

true
true
```
