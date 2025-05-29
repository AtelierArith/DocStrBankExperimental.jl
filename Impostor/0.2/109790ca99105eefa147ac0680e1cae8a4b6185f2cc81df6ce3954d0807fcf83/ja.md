```
credit_card_vendor(n::Integer = 1; kwargs...)
credit_card_vendor(options::Vector{<:AbstractString}, n::Integer; kwargs...)
```

`n` 個のクレジットカードベンダー名を生成します。

# 例

```@repl
julia> credit_card_vendor(3)
3-element Vector{String}:
 "American Express"
 "American Express"
 "Visa"
```
