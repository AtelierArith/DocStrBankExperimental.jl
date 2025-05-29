`coefficient(p::Mvp,m::Monomial)`

The coefficient of the polynomial `p` on the monomial `m`.

```julia-repl
julia> @Mvp x,y; p=(x-y)^3
Mvp{Int64}: x³-3x²y+3xy²-y³

julia> coefficient(p,Monomial_(:x=>2,:y=>1)) # coefficient on x²y
-3

julia> coefficient(p,Monomial()) # constant coefficient
0
```
