`coefficient(p::Mvp,m::Monomial)`

多項式 `p` のモノミアル `m` における係数。

```julia-repl
julia> @Mvp x,y; p=(x-y)^3
Mvp{Int64}: x³-3x²y+3xy²-y³

julia> coefficient(p,Monomial_(:x=>2,:y=>1)) # x²y の係数
-3

julia> coefficient(p,Monomial()) # 定数項
0
```
