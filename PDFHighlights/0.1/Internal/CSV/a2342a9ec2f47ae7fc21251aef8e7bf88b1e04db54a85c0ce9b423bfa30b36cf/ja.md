```
get_locations(csv::String) -> Vector{Int32}
```

CSVファイルから`Location`列の値を抽出します。

# 引数

  * `csv::String`: CSVファイルへの絶対パスまたは相対パス

# 戻り値

  * `Vector{Int32}`: ロケーション

# 例外

  * [`get_all`](@ref)からの例外

# 例

```jldoctest; output = false
using PDFHighlights
HEADER = PDFHighlights.Internal.Constants.HEADER

_file, io = mktemp()
println(io, HEADER, '\n', ",,,,5722")
flush(io)
file = _file * ".csv"
mv(_file, file)

get_locations(file) == Int32[5722]

# output

true
```
