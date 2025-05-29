```
losers(fmp)
```

最大の損失を出している銘柄を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。

詳細については [Most-Loser](https://site.financialmodelingprep.com/developer/docs/#Most-Loser-Stock-Companies) を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 最大の損失を出している銘柄を取得
data = losers(fmp)
```
