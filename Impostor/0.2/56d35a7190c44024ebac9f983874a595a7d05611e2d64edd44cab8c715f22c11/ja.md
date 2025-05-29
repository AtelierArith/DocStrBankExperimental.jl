```
credit_card_expiry(n::Integer = 1; kwargs...)
```

`n` 個のクレジットカードの有効期限エントリを生成します。例: `05/2029`。

# 例

```@repl
julia> credit_card_expiry(3)
3-element Vector{String}:
 "4/2014"
 "7/2013"
 "10/2010"
```
