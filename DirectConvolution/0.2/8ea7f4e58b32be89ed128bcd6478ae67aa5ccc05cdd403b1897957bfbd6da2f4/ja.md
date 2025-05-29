```
directConv!
```

畳み込みを計算します。

$$
\gamma[k]=\sum\limits_{i\in\Omega^\alpha}\alpha[i]\beta[k+\lambda i]
$$

以下の例は、`γ[5:10]` に `[0 0 1]` フィルタをインプレースで適用する方法を示しています。

```jldoctest
julia> β=[1:15;];

julia> γ=ones(Int,15);

julia> α=LinearFilter([0,0,1],0);

julia> directConv!(α,1,β,γ,5:10)

julia> hcat([1:length(γ);],γ)
15×2 Matrix{Int64}:
  1   1
  2   1
  3   1
  4   1
  5   7
  6   8
  7   9
  8  10
  9  11
 10  12
 11   1
 12   1
 13   1
 14   1
 15   1

```
