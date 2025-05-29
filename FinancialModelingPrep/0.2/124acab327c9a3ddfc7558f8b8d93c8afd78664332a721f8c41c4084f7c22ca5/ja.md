```
stock_screener(fmp, params...)
```

指定されたフィルターの検索結果を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Stock-Screener](https://site.financialmodelingprep.com/developer/docs/#Stock-Screener)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 市場資本が100mmを超え、ベータが1を超えるNASDAQのすべてのテクノロジー株を取得
data = stock_screener(fmp, marketCapMoreThan = 100000000, betaMoreThan = 1, sector = "Technology", exchange = "NASDAQ")

# カリフォルニアの価格が100を超える最初の100株を取得
data = stock_screener(fmp, country = "CA", priceMoreThan = 100, limit = 100)
```
