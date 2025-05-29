`bernoulli(n)` the `n`-th *Bernoulli number*  `Bₙ` as a `Rational{BigInt}`

`Bₙ`    is    defined    by   $B₀=1,   B_n=-\sum_{k=0}^{n-1}({n+1\choose k}B_k)/(n+1)$.  `Bₙ/n!` is the coefficient of  `xⁿ` in the power series of `x/(eˣ-1)`.  Except for `B₁=-1/2` the Bernoulli numbers for odd indices are zero.

```julia-repl
julia> bernoulli(4)
-1//30

julia> bernoulli(10)
5//66

julia> bernoulli(12) # there is no simple pattern in Bernoulli numbers
-691//2730

julia> bernoulli(50) # and they grow fairly fast
495057205241079648212477525//66
```
