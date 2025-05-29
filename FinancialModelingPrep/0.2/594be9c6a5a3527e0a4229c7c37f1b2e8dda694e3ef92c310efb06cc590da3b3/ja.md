```
nyse_schedule(fmp)
```

NYSEのスケジュールを含むJSON辞書を返します。市場の営業時間と市場の休日が含まれます。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。

詳細については、[NYSE-Schedule](https://site.financialmodelingprep.com/developer/docs/#NYSE-Holidays-and-Trading-Hours)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# NYSEの休日スケジュールを取得
data = nyse_schedule(fmp)[:stockMarketHolidays]
```
