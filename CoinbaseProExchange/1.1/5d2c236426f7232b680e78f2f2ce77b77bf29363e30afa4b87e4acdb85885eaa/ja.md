```
show_all_products(currency::String)
```

指定された通貨のすべての利用可能な製品のリストを取得します。

# 引数

  * `currency::String` : "EUR", "USD" (デフォルト), "GBP" など。

# 例

```julia-repl
julia> show_all_products("EUR")
40-element Vector{String}:
 "ETC-EUR"
 "SNX-EUR"
```
