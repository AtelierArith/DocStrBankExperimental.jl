```
hasse_invariant(S::ZZLocalGenus) -> Int
```

代表のハッセ不変量を返します。代表が対角行列 (a*1, ... , a*n) の場合、ハッセ不変量は

$$
\prod_{i < j}(a_i, a_j)_p
$$

です。
