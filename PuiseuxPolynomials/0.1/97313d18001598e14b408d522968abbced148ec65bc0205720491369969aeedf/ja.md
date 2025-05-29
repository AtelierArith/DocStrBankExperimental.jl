`valuation(m::Mvp[,v::Symbol])`

`Mvp`の`valuation`は、単項式の最小次数です。

第二引数に変数名を指定すると、`valuation`はその変数における多項式の評価を返します。

```julia-repl
julia> @Mvp x,y; a=x^2+x*y
Mvp{Int64}: x²+xy

julia> valuation(a), valuation(a,:y), valuation(a,:x)
(2, 0, 1)
```
