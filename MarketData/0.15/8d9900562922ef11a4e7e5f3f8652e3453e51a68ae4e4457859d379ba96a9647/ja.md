```
yahoo(symbol::AbstractString, opt::YahooOpt = YahooOpt())::TimeArray
yahoo(symbol::Symbol, opt::YahooOpt = YahooOpt())::TimeArray
```

これは、Yahoo Financeから過去の株価をダウンロードするためのラッパーです。

yahooメソッドは、文字列の形式で株名を受け取り、Yahoo Financeのティッカーに対応する`TimeSeries.TimeArray`を返します。引数を指定しない場合、デフォルトの過去の時系列はS&P 500です。

# 例

```julia
AAPL = yahoo(:AAPL)
SPX = yahoo("^GSPC")
NQ = yahoo("^IXIC")
```

```jl-repl
julia> start = DateTime(2018, 1, 1)
2018-01-01T00:00:00

julia> yahoo(:AAPL, YahooOpt(period1 = start))
655×6 TimeArray{Float64,2,Date,Array{Float64,2}} 2018-01-02 to 2020-08-07
...
```

# 参考文献

https://finance.yahoo.com

# 参照

  * fred()  セントルイス連邦準備銀行の金融および経済データセットにアクセスします。
  * ons()   国家統計局（ONS）から金融および経済時系列データをダウンロードするためのラッパーです。
