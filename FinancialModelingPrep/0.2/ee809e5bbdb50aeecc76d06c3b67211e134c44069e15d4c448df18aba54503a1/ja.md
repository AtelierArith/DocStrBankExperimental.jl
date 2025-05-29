```
press_releases(fmp, symbol, params...)
```

株式のプレスリリースを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep のインスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については [Press-Releases](https://site.financialmodelingprep.com/developer/docs/#Press-Releases) を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL のプレスリリースの最初のページを取得
data = press_releases(fmp, symbol = "AAPL", page = 0)
```
