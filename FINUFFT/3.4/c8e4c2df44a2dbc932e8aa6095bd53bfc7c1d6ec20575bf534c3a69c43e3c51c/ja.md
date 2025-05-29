```
nufft1d3(xj      :: Array{Float64} or Array{Float32}, 
         cj      :: Array{ComplexF64} or Array{ComplexF32}, 
         iflag   :: Integer, 
         eps     :: Real,
         sk      :: Array{Float64} or Array{Float32};
         kwargs...
        ) -> Array{ComplexF64}
```

タイプ3の1D複素非一様FFTを計算します。これは、相対精度epsで、迅速なアルゴリズムを介して計算されます：

```
         nj
f[k]  =  SUM   c[j] exp(+-i s[k] x[j]),      for k = 1, ..., nk
         j=1
```

# 入力

  * `xj`       R（実数直線）上の非一様ソースの位置、長さ-njベクトル。
  * `cj`       ソース強度の長さ-nj複素ベクトル。もしlength(cj)>njの場合、           サイズ`(nj,ntrans)`の行列を期待し、各列は同じソースとターゲットの位置で変換されます。
  * `iflag`    もし>=0の場合、指数関数で+符号を使用し、そうでなければ-符号を使用します。
  * `eps`      要求される相対精度（一般的に1e-15と1e-1の間）
  * `sk`       R上の非一様ターゲットの周波数位置、長さ-nkベクトル。
  * kwargs   （オプション）。`nufft_opts`およびhttps://finufft.readthedocs.io/en/latest/opts.htmlを参照してください。

# 出力

  * ターゲットでの値のサイズが`(nk,)`の複素ベクトルf、または、もし`ntrans>1`の場合、          サイズ`(nk,ntrans)`の行列。
