```
nufft3d2(xj      :: Array{Float64} or Array{Float32}, 
         yj      :: Array{Float64} or Array{Float32}, 
         zj      :: Array{Float64} or Array{Float32}, 
         iflag   :: Integer, 
         eps     :: Real,
         fk      :: Array{ComplexF64} or Array{ComplexF32};
         kwargs...
        ) -> Array{ComplexF64}
```

タイプ2の3D複素非一様FFTを計算します。これは、相対精度epsで、迅速なアルゴリズムを介して計算されます：

```
c[j] =   SUM   f[k1,k2,k3] exp(+/-i (k1 x[j] + k2 y[j] + k3 z[j]))
       k1,k2,k3
                       for j = 1,..,nj
 where sum is over -ms/2 <= k1 <= (ms-1)/2, -mt/2 <= k2 <= (mt-1)/2,
                  -mu/2 <= k3 <= (mu-1)/2.
```

# 入力

  * `xj`,`yj`,`zj` 非一様ターゲットの座標 [-3pi,3pi)^3 の立方体上で、各々が長さnjのベクトル
  * `fk`       複素フーリエ係数配列で、そのサイズが `(ms,mt,mu)` を設定します。          （各次元でopts.modeordによって与えられるモード順序。）          4D配列の場合、4次元が `ntrans` を設定し、各 `ntrans`          の3D配列は同じ非一様ターゲットで変換されます。
  * `iflag`    >=0 の場合、指数関数で + 記号を使用し、それ以外の場合は - 記号を使用します。
  * `eps`      要求される相対精度（一般的に1e-15と1e-1の間）
  * kwargs   （オプション）。`nufft_opts` および https://finufft.readthedocs.io/en/latest/opts.html を参照してください。

# 出力

  * サイズ `(nj,)` の複素ベクトル c がターゲットでの回答を提供します。あるいは、         `ntrans>1` の場合、サイズ `(nj,ntrans)` の行列になります。
