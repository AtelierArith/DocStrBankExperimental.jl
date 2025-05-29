```
get_titles(target::String) -> Vector{String}
```

CSVファイルが渡された場合は`Titles`列から値を取得し、ディレクトリが渡された場合は再帰的に見つかったすべてのPDFのタイトルを取得します。

# 引数

  * `target::String`: CSVファイルまたはPDFファイルのあるディレクトリ

# 戻り値

  * `Vector{String}`: タイトル

# 例外

  * [`NotCSVorDir`](@ref): 指定されたパスが`.csv`で終わらず、ディレクトリでもない
  * 例外: [`_get_titles_from_CSV`](@ref), [`_get_titles_from_PDF`](@ref)からの例外

# 例

```jldoctest; output = false
using PDFHighlights
HEADER = PDFHighlights.Internal.Constants.HEADER

path_to_pdf_dir = joinpath(pathof(PDFHighlights) |> dirname |> dirname, "test", "pdf")

(get_titles(path_to_pdf_dir) == ["A dummy PDF for tests"]) |> println

_file, io = mktemp()
println(io, HEADER, '\n', ",\"Girl, Interrupted\",,,1")
flush(io)
file = _file * ".csv"
mv(_file, file)

get_titles(file) == ["Girl, Interrupted"]

# output

true
true
```
