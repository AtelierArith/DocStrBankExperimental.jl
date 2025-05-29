```
insider_roster_statistics(fmp, symbol)
```

指定されたシンボルのインサイダー名簿統計を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Insider-Roster-Statistics](https://site.financialmodelingprep.com/developer/docs/#Stock-Insider-Trading)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL のインサイダー名簿統計を取得
data = insider_roster_statistics(fmp, "AAPL")
```
