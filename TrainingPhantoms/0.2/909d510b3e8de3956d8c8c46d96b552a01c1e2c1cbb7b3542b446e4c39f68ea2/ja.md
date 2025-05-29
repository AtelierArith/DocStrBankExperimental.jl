```
ellipsoidPhantom(
  N::NTuple{D,Int}; 
  rng::AbstractRNG = GLOBAL_RNG,
  numObjects::Int = rand(rng, 5:10),
  minRadius::Real=1.0,
  minValue::Real=0.1,
  allowOcclusion::Bool=false
)
```

複数の楕円体で構成されたファントムを生成します。

# 引数

  * `N`: ファントム画像のサイズ
  * `rng`: 擬似乱数生成器
  * `numObjects`: 生成する楕円の数
  * `minRadius`: ピクセル単位の最小半径
  * `minValue`: 単一の楕円の最小値
  * `allowOcclusion`: `true` の場合、楕円はその位置で小さい値を覆い隠します。つまり、新しい楕円は既存のオブジェクトに単純に追加されるのではなく、最大値が選択されます
  * `pixelMargin`: 画像の端からオブジェクトまでの最小距離

# 例

using GLMakie, TrainingPhantoms, StableRNGs

im = ellipsoidPhantom((51,51); rng=StableRNG(1))   f = Figure(size=(300,300))   ax = Axis3(f[1,1], aspect=:data)   volume!(ax, im, algorithm=:iso, isorange=0.13, isovalue=0.3, colormap=:viridis, colorrange=[0.0,0.2])
