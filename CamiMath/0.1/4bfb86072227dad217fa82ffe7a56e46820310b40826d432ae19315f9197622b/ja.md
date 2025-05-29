```
faulhaber_polynom(p::Integer [; msg=true])
```

次数 `p` の [`faulhaber_polynomial`](@ref) の係数のベクトル表現、

$$
   c=[c_0,⋯\ c_p],
$$

ここで $c_0=0,\ \ c_j=\frac{1}{p}{\binom{p}{p-j}}B_{p-j}$、$j∈\{ 1,⋯\ p\}$ です。$B_{p-j}$ は *偶数インデックスの規約* における [`bernoulliB`](@ref) です（ただし $B_1=+\frac{1}{2}$ ではなく $-\frac{1}{2}$ です）。

  * `msg` : 整数オーバーフロープロテクション (IOP) - 有効化時の警告

（`p > 36` の場合）

#### 例:

```
faulhaber_polynom(6)
7-element Vector{Rational{Int64}}:
  0//1
  0//1
 -1//12
  0//1
  5//12
  1//2
  1//6
```
