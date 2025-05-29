```
eigs(A, B; nev=6, ncv=max(20,2*nev+1), which=:LM, tol=0.0, maxiter=300, sigma=nothing, ritzvec=true, v0=zeros((0,)), check=0) -> (d,[v,],nconv,niter,nmult,resid)
```

行列 `A` と `B` の一般化固有値 `d` を計算します。これは、実対称行列または一般の非対称行列に対して、それぞれ暗黙的に再起動されたランチョス法またはアーノルディ法を使用します。詳細については、[マニュアル](@ref man-eigsgen)を参照してください。

`check = 0` の場合、最大反復回数が超過した場合にエラーが発生します（`info = 1`）。これは通常、ARPACKマニュアルに従ってすべての可能な固有値が見つかったことを意味します。`check = 1` の場合、`info = 1` のときに現在収束した固有値を返します。そして、`@warn` が表示されます。`check = 2` の場合、`info = 1` のときに現在収束した固有値を返します。
