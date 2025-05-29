```
market_risk_premiums(fmp)
```

各国の市場リスクプレミアムを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。

詳細については、[Market-Risk-Premium](https://site.financialmodelingprep.com/developer/docs/#Market-Risk-Premium)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# すべての市場リスクプレミアムを取得
data = market_risk_premiums(fmp)
```
