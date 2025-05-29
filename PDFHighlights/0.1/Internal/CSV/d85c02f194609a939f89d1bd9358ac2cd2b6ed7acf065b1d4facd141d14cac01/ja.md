```
get_notes(csv::String) -> Vector{String}
```

CSVファイルから`Note`列の値を抽出します。

# 引数

  * `csv::String`: CSVファイルへの絶対パスまたは相対パス

# 戻り値

  * `Vector{String}`: ノート

# 例外

  * [`get_all`](@ref)からの例外

# 例

```jldoctest; output = false
using PDFHighlights
HEADER = PDFHighlights.Internal.Constants.HEADER

_file, io = mktemp()
println(io, HEADER, '\n', ",,,Journal,")
flush(io)
file = _file * ".csv"
mv(_file, file)

get_notes(file) == ["Journal"]

# output

true
```
