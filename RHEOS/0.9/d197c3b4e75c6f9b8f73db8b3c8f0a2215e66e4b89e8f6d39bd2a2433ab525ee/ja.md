```
importcsv(filepath::String, interface::Interface; delimiter = ',', header = false, comment = "Imported from csv file", savelog = true, kwargs...)
```

生データを `Interface` を使用して応力とひずみに変換するためのインポート関数。力/変位データを含むcsvの列番号は、`interface` の対応するシンボルを使用してキーワード引数として指定する必要があります。

# 例

```julia-repl
julia> importcsv("myfile.csv", AFM(2e-6), t=1, d=2, f=3)
```
