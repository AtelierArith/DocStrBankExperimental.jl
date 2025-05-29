`valuation(c::Union{Integer,Rational{<:Integer},p::Integer)`  `p`-進数  評価関数 `c` の (cを割る最大の `p` の累乗; `Rational` の場合、分子の評価から分母の評価を引いたもの)。

```julia-repl
julia> valuation.(24,(2,3,5))
(3, 1, 0)
```
