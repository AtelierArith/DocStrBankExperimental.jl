```
search_symbol(fmp, symbol, params...)
```

指定されたシンボルとフィルターの検索結果を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Symbol-Search](https://site.financialmodelingprep.com/developer/docs/#Ticker-Search)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# シンボルが AA で、取引所が NASDAQ の最初の 10 件の一致を取得
data = search_symbol(fmp, "AA", limit = 10, exchange = "NASDAQ")
```
