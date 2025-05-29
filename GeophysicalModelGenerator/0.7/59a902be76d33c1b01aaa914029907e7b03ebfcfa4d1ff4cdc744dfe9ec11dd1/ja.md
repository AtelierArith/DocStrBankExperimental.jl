```
parse_columns_CSV(data_file, num_columns)
```

これは、`CSV.File`で読み込まれたCSVファイルから数値を解析します。これは、CSVファイルに文字列（例：駅名）と数値（緯度/経度/高さ）が含まれており、数値のみが必要な場合に便利です。

# 例

この例では、データが18行目から始まり、列がスペースで区切られており、データが最大4列含まれていると仮定しています：

```julia-repl
julia> using CSV
julia> data_file        =   CSV.File("FileName.txt",datarow=18,header=false,delim=' ')
julia> data = parse_columns_CSV(data_file, 4)
```
