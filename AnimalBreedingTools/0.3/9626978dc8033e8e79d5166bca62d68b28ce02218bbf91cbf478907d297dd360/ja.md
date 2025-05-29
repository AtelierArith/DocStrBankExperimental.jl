```
x = solve_pcg(A,b; maxiter=5000,eps=1e-15,reset=50,verbose=false)
```

対称正定値方程式系を解きます：`A`はスパースの左辺、`b`は右辺のベクトルです。ヤコビ前処理子（`diag(A)`）が使用されます。最大反復回数は`maxiter`で指定されます。収束基準`eps`は`norm(b-A*x)/norm(b)`です。残差ベクトルは`reset`ラウンドごとに再計算されます。詳細は`verbose=true`で表示されます。

```juliadoctest
julia> x = solve_pcg(A,b)
```
