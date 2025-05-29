```
nufft1d1(xj      :: Array{Float64} or Array{Float32}, 
         cj      :: Array{ComplexF64} or Array{ComplexF32}, 
         iflag   :: Integer, 
         eps     :: Real,
         ms      :: Integer;
         kwargs...
        ) -> Array{ComplexF64} or Array{ComplexF32}
```

タイプ1の1D複素非一様FFTを計算します。これは、相対精度epsで、迅速なアルゴリズムを介して計算されます：

```
          nj
f(k1) =  SUM c[j] exp(+/-i k1 x(j))  for -ms/2 <= k1 <= (ms-1)/2
         j=1
```

# 入力

  * `xj`      区間[-3pi,3pi)上の非一様ソースの位置、長さnj
  * `cj`      ソース強度の長さ-njの複素ベクトル。もしlength(cj)>njの場合、同じソース位置で変換されるベクトルのスタック（例えば、nj*ntrans行列）を期待します。
  * `iflag`   もし>=0の場合、指数関数で+符号を使用し、そうでなければ-符号を使用します。
  * `eps`     要求される相対精度（一般的に1e-15と1e-1の間）
  * `ms`      計算されるフーリエモードの数、偶数または奇数である可能性があります；いずれの場合も、モード範囲は[-ms/2, (ms-1)/2]にある整数です。
  * kwargs  （オプション）。`nufft_opts`およびhttps://finufft.readthedocs.io/en/latest/opts.htmlを参照してください。

# 出力

  * サイズ`(ms,)`のフーリエ係数fの複素ベクトル、または、もし`ntrans>1`の場合、サイズ`(ms,ntrans)`の行列。
