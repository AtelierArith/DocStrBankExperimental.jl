```
search_name(fmp, name, params...)
```

指定された名前とフィルターの検索結果を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `name::String`: 会社名。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Name-Search](https://site.financialmodelingprep.com/developer/docs/#Ticker-Search)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 名前が Meta で、取引所が NASDAQ の最初の 10 件の一致を取得
data = search_name(fmp, "Meta", limit = 10, exchange = "NASDAQ")
```
