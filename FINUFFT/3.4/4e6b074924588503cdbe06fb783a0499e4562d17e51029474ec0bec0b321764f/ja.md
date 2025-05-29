```
nufft2d2(xj      :: Array{Float64} or Array{Float32}, 
         yj      :: Array{Float64} or Array{Float32}, 
         iflag   :: Integer, 
         eps     :: Real,
         fk      :: Array{ComplexF64} or Array{ComplexF32};
         kwargs...
        ) -> Array{ComplexF64}
```

タイプ2の2D複素非一様FFTを計算します。これは、相対精度epsで、迅速なアルゴリズムを介して計算されます：

```
c[j] =  SUM   f[k1,k2] exp(+/-i (k1 x[j] + k2 y[j]))  for j = 1,..,nj
       k1,k2
 ここで、合計は -ms/2 <= k1 <= (ms-1)/2, -mt/2 <= k2 <= (mt-1)/2 の範囲です、
```

# 入力

  * `xj`,`yj`   [-3pi,3pi)^2の正方形上の非一様ターゲットの座標で、        各々は長さnjのベクトルです
  * `fk`      複素フーリエ係数行列で、そのサイズが(ms,mt)を決定します。        （各次元でopts.modeordによって与えられるモード順序。）        3D配列の場合、3番目の次元が`ntrans`を設定し、各`ntrans`        行列は同じ非一様ターゲットで変換されます。
  * `iflag`   もし>=0であれば、指数関数に+符号を使用し、そうでなければ-符号を使用します。
  * `eps`     要求される相対精度（一般的には1e-15と1e-1の間）
  * kwargs  （オプション）。`nufft_opts`およびhttps://finufft.readthedocs.io/en/latest/opts.htmlを参照してください。

# 出力

  * ターゲットでの回答の複素サイズ`(nj,)`ベクトルc、または、        `ntrans>1`の場合、サイズ`(nj,ntrans)`の行列。
