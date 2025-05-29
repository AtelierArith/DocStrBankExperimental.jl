```
nufft1d2(xj      :: Array{Float64} or Array{Float32}, 
         iflag   :: Integer, 
         eps     :: Real,
         fk      :: Array{ComplexF64} or Array{ComplexF32};
         kwargs...
        ) -> Array{ComplexF64}
```

タイプ2の1D複素非一様FFTを計算します。これは、相対精度epsで、高速アルゴリズムを介して計算します：

```
c[j] = SUM   f[k1] exp(+/-i k1 x[j])      for j = 1,...,nj
        k1
 ここで、合計は -ms/2 <= k1 <= (ms-1)/2 の範囲です。
```

# 入力

  * `xj`      非一様ターゲットの位置 [-3pi,3pi) の間、長さ nj
  * `fk`      複素フーリエ係数。ベクトルの場合、長さは ms を設定します（モード順序は opts.modeord によって与えられます）。行列の場合、各列は同じ非一様ターゲットで変換されます。
  * `iflag`   0以上の場合、指数関数に + の符号を使用し、それ以外の場合は - の符号を使用します。
  * `eps`     要求される相対精度（一般的には 1e-15 と 1e-1 の間）
  * kwargs  （オプション）。`nufft_opts` および https://finufft.readthedocs.io/en/latest/opts.html を参照してください。

# 出力

  * ターゲットでの回答の複素 `(nj,)` ベクトル c、または `ntrans>1` の場合、サイズ `(nj,ntrans)` の行列。
