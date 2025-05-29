```
parse_opendss(file::String; method::Union{String,Missing}=missing, kwargs...)
```

オープンDSSデータファイルをPowerModelsDistributionのparse_file関数を使用して解析し、故障研究に特有のいくつかの追加データ変換を加えたエンジニアリングデータモデルに変換します。

`method`は`missing`または`"PMD"`である必要があります。

`kwargs`はPowerModelsDistributionの`parse_file`関数からの有効なキーワード引数であれば何でも使用できます。
