```
(s::Space)(n::Integer)
```

`[zeros(n); 1]`のスパース表現を係数とする`Fun`を返します。結果は主に特定の点で評価されることを意図しています。

直交多項式空間の場合、結果は通常`n`-番目の基底関数を表します。

# 例

```jldoctest
julia> Chebyshev()(2) == Fun(Chebyshev(), [0, 0, 1])
true
```
