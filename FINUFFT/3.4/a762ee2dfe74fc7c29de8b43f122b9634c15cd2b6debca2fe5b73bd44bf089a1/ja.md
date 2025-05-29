```
nufft3d1(xj      :: Array{Float64} or Array{Float32}, 
         yj      :: Array{Float64} or Array{Float32}, 
         zj      :: Array{Float64} or Array{Float32}, 
         cj      :: Array{ComplexF64} or Array{ComplexF32}, 
         iflag   :: Integer, 
         eps     :: Real,
         ms      :: Integer,
         mt      :: Integer,
         mu      :: Integer;
         kwargs...
        ) -> Array{ComplexF64}
```

タイプ1の3D複素非一様FFTを計算します。これは、相対精度epsで、迅速なアルゴリズムを介して計算されます：

```
                  nj
f[k1,k2,k3] =    SUM  c[j] exp(+-i (k1 x[j] + k2 y[j] + k3 z[j]))
                 j=1

for -ms/2 <= k1 <= (ms-1)/2,  -mt/2 <= k2 <= (mt-1)/2,
    -mu/2 <= k3 <= (mu-1)/2.
```

# 入力

  * `xj`,`yj`,`zj` 非一様ソースの座標 [-3pi,3pi)^3 の立方体上の各長さ-njベクトル
  * `cj`       ソース強度の長さ-nj複素ベクトル。もし length(cj)>nj の場合、同じソース位置で変換されるベクトルのスタック（例：nj*ntrans行列）を期待します。
  * `iflag`    もし >=0 の場合、指数に + 記号を使用し、そうでない場合は - 記号を使用します。
  * `eps`      要求される相対精度（一般的に 1e-15 と 1e-1 の間）
  * `ms`,`mt`,`mu` x,y,z で要求されるフーリエモードの数；各々は偶数または奇数である可能性があります。いずれの場合も、モード範囲は [-m/2, (m-1)/2] にある整数です。
  * kwargs  （オプション）。`nufft_opts` および https://finufft.readthedocs.io/en/latest/opts.html を参照してください。

# 出力

  * サイズ `(ms,mt,mu)` の複素数配列 f のフーリエ係数（各次元で opts.modeord によって与えられる順序；`ms` が最も速く、`mu` が最も遅い）、または `ntrans>1` の場合、サイズ `(ms,mt,mu,ntrans)` の4D配列。
