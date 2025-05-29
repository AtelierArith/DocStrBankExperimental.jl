```
get_quotes(ticker)
get_quotes(ticker::Array)
```

シンボルの引用を取得します: https://developer.tdameritrade.com/quotes/apis/get/marketdata/{symbol}/quotes

`ticker` は単一の `String` または `Array` または複数の `String` であることができます。

# 例

```julia
get_quotes("GE")
get_quotes(["BA","GE"])
```
