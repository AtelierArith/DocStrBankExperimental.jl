```
Ticker(x::String)
```

ティッカー識別子を作成します。

# 例

```jldoctest; setup = :(using FinancialSymbology)
julia> ticker_id = Ticker("AAPL US Equity")
"AAPL US Equity"
```
