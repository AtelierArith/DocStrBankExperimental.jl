```
insider_trades(fmp, params...)
```

インサイダー取引を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Insider-Trading](https://site.financialmodelingprep.com/developer/docs/#Stock-Insider-Trading)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 最も最近のインサイダー購入と売却を取得
data = insider_trades(fmp, transactionType = ["P-Purchase", "S-Sale"], page = 0)

# AAPL の最も最近のインサイダー取引を取得
data = insider_trades(fmp, symbol = "AAPL", page = 0)
```
