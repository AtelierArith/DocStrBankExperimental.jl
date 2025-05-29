```
get_all(csv::String) -> Tuple{
    Vector{String},
    Vector{String},
    Vector{String},
    Vector{String},
    Vector{Int32},
}
```

CSVファイルからすべての列の値を抽出します。

# 引数

  * `csv::String`: CSVファイルへの絶対パスまたは相対パス

# 戻り値

  * `Tuple{Vector{String}, Vector{String}, Vector{String}, Vector{String}, Vector{Int32}}`: ハイライト、タイトル、著者、ノート、および場所

# 例外

  * [`IntegrityCheckFailed`](@ref): テーブルの整合性をチェック中に別の例外がスローされました
  * [`initialize`](@ref) からの例外

# 例

```jldoctest; output = false
using PDFHighlights
HEADER = PDFHighlights.Internal.Constants.HEADER

_file, io = mktemp()
row = string(
    "The world didn't stop spinning,",
    "\"Girl, Interrupted\",",
    "Susanna Kaysen,",
    "Journal,",
    "5722",
)
println(io, HEADER, '\n', row)
flush(io)
file = _file * ".csv"
mv(_file, file)

get_all(file) == (
    ["The world didn't stop spinning"],
    ["Girl, Interrupted"],
    ["Susanna Kaysen"],
    ["Journal"],
    [5722],
)

# output

true
```
