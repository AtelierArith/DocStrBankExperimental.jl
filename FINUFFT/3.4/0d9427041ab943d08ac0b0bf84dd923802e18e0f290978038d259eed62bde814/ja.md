```
nufft2d3(xj      :: Array{Float64} or Array{Float32}, 
         yj      :: Array{Float64} or Array{Float32},
         cj      :: Array{ComplexF64} or Array{ComplexF32}, 
         iflag   :: Integer, 
         eps     :: Real,
         sk      :: Array{Float64} or Array{Float32},
         tk      :: Array{Float64} or Array{Float32};
         kwargs...
        ) -> Array{ComplexF64}
```

タイプ3の2D複素非一様FFTを計算します。これは、相対精度epsで、迅速なアルゴリズムを介して計算されます：

```
         nj
f[k]  =  SUM   c[j] exp(+-i (s[k] x[j] + t[k] y[j])),  for k = 1, ..., nk
         j=1
```

# 入力

  * `xj`,`yj`    R^2における非一様ソースの座標で、それぞれ長さnjのベクトルです。
  * `cj`    ソース強度の複素ベクトル `(nj,)`。もし length(cj)>nj の場合、          `(nj,ntrans)` 行列を期待し、各列は同じソースとターゲットの位置で変換されます。
  * `iflag`    もし >=0 の場合、指数に + 記号を使用し、そうでなければ - 記号を使用します。
  * `eps`      要求される相対精度（一般的に 1e-15 と 1e-1 の間）
  * `sk`,`tk`    R^2における非一様ターゲットの周波数座標で、それぞれ長さnkのベクトルです。
  * kwargs   （オプション）。`nufft_opts` および https://finufft.readthedocs.io/en/latest/opts.html を参照してください。

# 出力

  * ターゲットでの値の複素ベクトルサイズ `(nk,)`、または `ntrans>1` の場合、          サイズ `(nk,ntrans)` の行列。
