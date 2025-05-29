```
key_metrics(fmp, symbol, period, params...)
```

指定されたシンボルの主要指標を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `period::String`: `REPORTING_PERIODS` オプション。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Key-Metrics](https://site.financialmodelingprep.com/developer/docs/#Company-Key-Metrics)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 過去30年間の AAPL の主要指標を ttm で取得
data = key_metrics(fmp, "AAPL", period = REPORTING_PERIODS.ttm, limit = 30)
```
