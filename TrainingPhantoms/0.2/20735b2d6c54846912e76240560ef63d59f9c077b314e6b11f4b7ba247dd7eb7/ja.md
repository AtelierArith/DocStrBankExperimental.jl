```
vesselPhantom(N::NTuple{D,Int}; oversampling=2, kargs...)
```

ランダムな血管ファントムを生成します。

# 引数

  * N: Dタプルとして与えられる画像サイズ
  * oversampling: ファントムのオーバーサンプリング係数。デフォルトは2。
  * rng: 擬似乱数生成器
  * kernelWidth: ファントムの平滑化に使用されるガウスカーネルの幅（標準偏差）（ピクセル単位）。何も指定されない場合は、ランダムな値が選ばれます。
  * kargs...: `vesselPath` の残りのキーワード引数

# 例

using GLMakie, TrainingPhantoms, StableRNGs

im = vesselPhantom((51,51,51);            start=(1, 25, 25), angles=(0.0, 0.0),            diameter=2.5, splitProb=0.4, changeProb=0.3,            maxChange=0.3, splitnr=1, maxNumSplits=1, rng StableRNG(123));

f = Figure(size=(300,300))   ax = Axis3(f[1,1], aspect=:data)   volume!(ax, im, algorithm=:iso, isorange=0.13, isovalue=0.3, colormap=:viridis, colorrange=[0.0,0.2])
