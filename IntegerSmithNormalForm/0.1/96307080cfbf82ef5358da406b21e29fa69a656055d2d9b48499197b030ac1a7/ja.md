```
(S,B,T) = snf!(A)
```

スミス標準形 `B = SAT` を計算します。ここで、`B` は `A` のインプレースで計算されます。

行列 `S,B,T` は整数行列であり、

  * |det(S)| = |det(T)| = 1 であり、B = SAT
  * B は対角行列です
  * B[i,i] >= 0 すべての i に対して
  * B[i,i] はすべての j > i に対して B[j,j] を割ります
