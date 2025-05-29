```
credit_card_number(n::Integer = 1; kwargs...)
credit_card_number(options::Vector{<:AbstractString}, n::Integer; kwargs...)
credit_card_number(mask::Vector{<:AbstractString}; kwargs...)
```

クレジットカードベンダーに従って有効なクレジットカード番号を生成します。利用可能なベンダーは次のとおりです：

  * `"Visa"`
  * `"American Express"`
  * `"MasterCard"`

# パラメータ

  * `n::Integer = 1`: 生成するクレジットカード番号の数。
  * `options::Vector{<:AbstractString}`: 生成される可能な値を制限するオプションを含むベクター。
  * `mask::Vector{<:AbstractString}`: 要素ごとのオプション制限を持つマスクベクター。

# Kwargs

  * `formatted::Bool`: 生のクレジットカード番号を返すか *e.g.* `"3756808757861311"`、または出力をフォーマットするか *e.g.* `"3756-8087-5786-1311"`。

# 例

```@repl
julia> credit_card_number()
"5186794250685172"

julia> credit_card_number(; formatted = true)
"4046-7508-2101-2729"
```
