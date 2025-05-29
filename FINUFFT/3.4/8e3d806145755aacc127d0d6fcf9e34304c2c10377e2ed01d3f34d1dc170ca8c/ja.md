```
nufft3d3(xj      :: Array{Float64} or Array{Float32}, 
         yj      :: Array{Float64} or Array{Float32},
         zj      :: Array{Float64} or Array{Float32},
         cj      :: Array{ComplexF64} or Array{ComplexF32}, 
         iflag   :: Integer, 
         eps     :: Real,
         sk      :: Array{Float64} or Array{Float32},
         tk      :: Array{Float64} or Array{Float32},
         uk      :: Array{Float64} or Array{Float32};
         kwargs...
        ) -> Array{ComplexF64}
```

タイプ3の3D複素非一様FFTを計算します。これは、高速アルゴリズムを介して、相対精度epsで計算します：

```
         nj
f[k]  =  SUM   c[j] exp(+-i (s[k] x[j] + t[k] y[j] + u[k] z[j])),
         j=1
                         for k = 1, ..., nk
```

# 入力

  * `xj`,`yj`,`zj` R^3における非一様ソースの座標で、それぞれ長さnjのベクトルです。
  * `cj`     ソース強度の複素数`(nj,)`ベクトル。もしlength(cj)>njの場合、同じソースとターゲットの位置で変換される'(nj,ntrans)'行列を期待します。
  * `iflag`    もし>=0の場合、指数に+符号を使用し、そうでなければ-符号を使用します。
  * `eps`      要求される相対精度（一般的に1e-15と1e-1の間）
  * `sk`,`tk,`uk` R^3における非一様ターゲットの周波数座標で、それぞれ長さnkのベクトルです。
  * kwargs   （オプション）。`nufft_opts`およびhttps://finufft.readthedocs.io/en/latest/opts.htmlを参照してください。

# 出力

  * サイズ`(nk,)`の複素ベクトルfのターゲットでの値、または、もし`ntrans>1`の場合、サイズ`(nk,ntrans)`の行列。
