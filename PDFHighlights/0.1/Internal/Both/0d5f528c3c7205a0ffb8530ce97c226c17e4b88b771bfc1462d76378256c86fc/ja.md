```
get_authors(target::String) -> Vector{String}
```

CSVファイルが渡された場合は`Authors`列から値を取得し、ディレクトリが渡された場合は再帰的に見つかったすべてのPDFの著者を取得します。

# 引数

  * `target::String`: CSVファイルまたはPDFファイルのあるディレクトリ

# 戻り値

  * `Vector{String}`: 著者

# 例外

  * [`NotCSVorDir`](@ref): 指定されたパスが`.csv`で終わらず、ディレクトリでもない
  * 例外: [`_get_authors_from_CSV`](@ref), [`_get_authors_from_PDF`](@ref)からの例外

# 例

```jldoctest; output = false
using PDFHighlights
HEADER = PDFHighlights.Internal.Constants.HEADER

path_to_pdf_dir = joinpath(pathof(PDFHighlights) |> dirname |> dirname, "test", "pdf")

(get_authors(path_to_pdf_dir) == ["Pavel Sobolev"]) |> println

_file, io = mktemp()
println(io, HEADER, '\n', ",,Susanna Kaysen,,1")
flush(io)
file = _file * ".csv"
mv(_file, file)

get_authors(file) == ["Susanna Kaysen"]

# output

true
true
```
