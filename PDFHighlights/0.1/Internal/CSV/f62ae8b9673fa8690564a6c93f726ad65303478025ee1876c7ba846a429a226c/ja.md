```
initialize(csv::String) -> Nothing
```

`csv`パスに沿ったファイルが存在しない場合は、それを作成してヘッダーを書き込みます。存在するが空の場合も同様に行います。存在し、空でない場合は、構造的な正しさを確認します。

# 引数

  * `csv::String`: CSVファイルへの絶対パスまたは相対パス

# 例外

  * [`NotCSV`](@ref): 指定されたパスが`.csv`で終わっていません
  * [`_check`](@ref)からの例外

# 例

```jldoctest; output = false
using PDFHighlights
HEADER = PDFHighlights.Internal.Constants.HEADER

_file, _ = mktemp()
file = _file * ".csv"
mv(_file, file)

initialize(file)

open(file, "r") do io
    readlines(io) == [HEADER]
end

# output

true
```
