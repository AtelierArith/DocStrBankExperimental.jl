```
insider_trading_types(fmp)
```

インサイダー取引の取引タイプを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。

詳細については、[Insider-Trading](https://site.financialmodelingprep.com/developer/docs/#Stock-Insider-Trading)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# インサイダー取引イベントのタイプを取得
data = insider_trading_types(fmp)
```
