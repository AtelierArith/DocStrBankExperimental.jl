`bernoulli(n)` は `n` 番目の *ベルヌーイ数* `Bₙ` を `Rational{BigInt}` として返します。

`Bₙ` は $B₀=1, B_n=-\sum_{k=0}^{n-1}({n+1\choose k}B_k)/(n+1)$ によって定義されます。 `Bₙ/n!` は `x/(eˣ-1)` の冪級数における `xⁿ` の係数です。 `B₁=-1/2` を除いて、奇数インデックスのベルヌーイ数はゼロです。

```julia-repl
julia> bernoulli(4)
-1//30

julia> bernoulli(10)
5//66

julia> bernoulli(12) # ベルヌーイ数には単純なパターンはありません
-691//2730

julia> bernoulli(50) # そしてそれらはかなり速く成長します
495057205241079648212477525//66
```
