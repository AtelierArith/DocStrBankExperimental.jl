```
insider_roster(fmp, symbol)
```

指定されたシンボルのインサイダー名簿を含むJSONテーブルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Insider-Roster](https://site.financialmodelingprep.com/developer/docs/#Stock-Insider-Trading)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLのインサイダー名簿を取得
data = insider_roster(fmp, "AAPL")
```
