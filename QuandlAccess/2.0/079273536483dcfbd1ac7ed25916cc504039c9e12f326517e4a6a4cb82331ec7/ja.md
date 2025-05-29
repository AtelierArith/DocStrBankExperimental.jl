```
Quandl
```

Quandl.comからデータをクエリするための主なアクセスオブジェクトです。

# 例

```julia
quandl(TimeSeries("ML/BBY"))
quandl(TimeSeries("ML/BBY"); start_date = Date(2020,1,1), end_date = Date(2020,1,5))
quandl(TimeSeries("ML/BBY"); collapse = "weekly")
quandl(TimeSeries("ML/BBY"); transform = "diff")
quandl(TimeSeries("ML/BBY"); order = "asc")

quandl(Table("ETFG/FUND"), filters = [eq("ticker", "SPY")])
quandl(Table("ETFG/FUND"), filters = [eq("ticker", "SPY")], columns = ["ticker", "nav"])
quandl(Table("ETFG/FUND"), filters = [eq("ticker", "SPY"), gt("as_of_date", "2018-01-09")])
```
