```
gls_pair_radial_fun(pair_corr_distance::Function, a12::T; polynomial_order::Int, mesh_size::Int)
```

関数 `gls_fun` を返します。任意の放射距離 `r1` と `r2` に対して、`gls = gls_fun(r1,r2)` となり、ここで `gls` はペア相関のためのレジェンドル係数の配列です。

数学的には、次のように表されます。$g(r_1,r_2,\cos \theta_{12}) = \sum_{\ell_1 =0} \frac{2\ell_1 + 1}{4\pi} gls[\ells+1] P_{\ell_1}(\cos \theta_{12})$、ここで $g(r_1,r_2,\cos \theta_{12})$ は放射対称ペア相関であり、放射距離 $r_1$ と $r_2$、および二つの位置ベクトル間の角度 $\theta_{12}$ のみに依存します。

関数 `gls_fun` は関数 `pair_corr_distance` から計算され、`pair_corr_distance(sqrt(r1^2 + r2^2 - 2r1 * r2 * cos(θ12)))` がペア相関を与えます。 ```
