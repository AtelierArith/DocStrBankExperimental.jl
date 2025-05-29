```julia
function ∑∑of²(x::UniData)
```

`x`の要素の合計と合計の二乗を1回のパスで計算し、2タプルとして返します。

*例*

```julia
using PermutationTests
x=randn(10)
s, s² = ∑∑of²(x)
```
