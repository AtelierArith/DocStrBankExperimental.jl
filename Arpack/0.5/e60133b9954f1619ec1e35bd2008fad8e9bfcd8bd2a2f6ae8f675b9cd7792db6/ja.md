```
svds(A; nsv=6, ritzvec=true, tol=0.0, maxiter=1000, ncv=2*nsv, v0=zeros((0,))) -> (SVD([left_sv,] s, [right_sv,]), nconv, niter, nmult, resid, check=0)
```

行列 `A` の最大特異値 `s` を、[`eigs`](@ref) から派生した暗黙的に再起動されたランチョス反復法を使用して計算します。詳細については [the manual](@ref man-svds) を参照してください。

`check = 0` の場合、最大反復回数が超過した場合にエラーがスローされます（`info = 1`）。これは通常、ARPACK マニュアルに従ってすべての可能な固有値が見つかったことを意味します。`check = 1` の場合、`info = 1` のときに現在収束した固有値を返します。そして、`@warn` が表示されます。`check = 2` の場合、`info = 1` のときに現在収束した固有値を返します。
