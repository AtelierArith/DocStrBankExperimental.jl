```
sample_points_chebyshev_mod(d, a = -1, b = 1; T=BigFloat) -> Vector{T}
```

区間 [a,b] における d+1 の修正されたチェビシェフ点を生成します。チェビシェフ点は cos(pi/(2(d+1))) で割られます。
