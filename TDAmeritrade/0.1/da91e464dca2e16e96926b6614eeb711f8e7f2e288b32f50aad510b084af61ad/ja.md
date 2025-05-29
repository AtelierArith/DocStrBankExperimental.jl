```
price_history(ticker; kwargs...)
```

指定されたティッカーの価格履歴を取得します。`ticker`を除くすべての引数は、TD APIによって指定されたデフォルト値を持ちます:  https://developer.tdameritrade.com/price-history/apis/get/marketdata/{symbol}/pricehistory

# オプションのkwargs:

periodType period frequencyType frequency endDate startDate needExtendedHoursData

# 例

```julia
using Dates

price_history("GE", Minute(1), Day(1)) # 過去1日のティック = 1日
price_history("GE", Day(1), Year(2)) # 過去2年のティック = 1日
price_history("AAPL", Day(1), now()-Day(1), now())
```
