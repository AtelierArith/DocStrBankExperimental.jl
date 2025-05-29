Download stock price data from Yahoo! Finance into a TS object.

`yahoo(symb::String; from::String="1900-01-01", thru::String=string(Dates.today()), freq::String="d", event::String="history", crumb_tuple::Tuple{SubString{String}, Dict{String, HTTP.Cookie}}=yahoo_get_crumb())::TS`

# Arguments

  * `symb` ticker symbol of the stock
  * `from` starting date of the historical data request (string formatted as yyyy-mm-dd)
  * `thru` ending date of the historical data request (string formatted as yyyy-mm-dd)
  * `freq` frequency interval of the requested dowload (valid options are "d" for daily, "wk" for weekly, and "mo" for monthly)
  * `event` type of data download to request (valid options are "history" for standard historical price data, "div" for dividend payments, and "split" for stock splits)
  * `crumb_tuple` workaround to provide crumbs/cookies for the new Yahoo Finance portal (which requires such data to fulfill the requests)

# Example

```
julia> yahoo("AAPL", from="2010-06-09", thru=string(Dates.today()), freq="wk")
356x6 Temporal.TS{Float64,Date}: 2010-06-09 to 2017-03-27
Index       Open    High    Low     Close   Volume      AdjClose
2010-06-09  251.47  253.86  242.2   253.51  1.813954e8  32.8446
2010-06-14  255.96  275.0   254.01  274.07  1.814594e8  35.5084
2010-06-21  277.69  279.01  265.81  266.7   1.763214e8  34.5535
2010-06-28  266.93  269.75  243.2   246.94  2.087241e8  31.9934
2010-07-06  251.0   262.9   246.16  259.62  1.525786e8  33.6362
⋮
2017-02-27  137.14  140.28  136.28  139.78  2.54267e7   139.78
2017-03-06  139.37  139.98  137.05  139.14  1.97315e7   139.14
2017-03-13  138.85  141.02  138.82  139.99  2.41057e7   139.99
2017-03-20  140.4   142.8   139.73  140.64  2.54857e7   140.64
2017-03-27  139.39  144.49  138.62  144.12  2.86449e7   144.12
```
