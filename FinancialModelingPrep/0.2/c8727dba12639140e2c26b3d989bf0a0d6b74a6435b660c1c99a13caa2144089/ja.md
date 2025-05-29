```
mergers_and_acquisitions_search(fmp, params...)
```

マージと買収の検索結果を含むJSONテーブルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Mergers-and-Acquisitions](https://site.financialmodelingprep.com/developer/docs/#MERGER-AND-ACQUISITION)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# マージと買収を検索
data = mergers_and_acquisitions_search(fmp, name = "Syros")
```
