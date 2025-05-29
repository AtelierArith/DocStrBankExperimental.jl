```
nufft2d1(xj      :: Array{Float64} or Array{Float32}
         yj      :: Array{Float64} or Array{Float32}, 
         cj      :: Array{ComplexF64} or Array{ComplexF32}, 
         iflag   :: Integer, 
         eps     :: Real,
         ms      :: Integer,
         mt      :: Integer;
         kwargs...
        ) -> Array{ComplexF64}
```

タイプ1の2D複素非一様FFTを計算します。これは、相対精度epsで、迅速なアルゴリズムを介して計算されます：

```
              nj
f[k1,k2] =   SUM  c[j] exp(+-i (k1 x[j] + k2 y[j]))
             j=1

- ms/2 <= k1 <= (ms-1)/2,  -mt/2 <= k2 <= (mt-1)/2.
```

# 入力

  * `xj`,`yj`   [-3pi,3pi)^2の正方形上の非一様ソースの座標、各々が長さ-njのベクトル
  * `cj`      長さ-njの複素ベクトルでソースの強度。もしlength(cj)>njであれば、同じソース位置で変換されるベクトルのスタック（例：nj*ntransの行列）を期待します。
  * `iflag`   もし>=0であれば、指数に+符号を使用し、そうでなければ-符号を使用します。
  * `eps`     要求される相対精度（一般的に1e-15と1e-1の間）
  * `ms`,`mt`   xおよびyで要求されるフーリエモードの数；各々は偶数または奇数である可能性があります。いずれの場合も、モード範囲は[-m/2, (m-1)/2]の整数です。
  * kwargs  （オプション）、`nufft_opts`およびhttps://finufft.readthedocs.io/en/latest/opts.htmlを参照してください。

# 出力

  * サイズ `(ms,mt)` の複素フーリエ係数fの行列（各次元でopts.modeordによって与えられる順序；`ms`は速く、`mt`は遅い）、または、もし`ntrans>1`であれば、サイズ `(ms,mt,ntrans)` の配列。
