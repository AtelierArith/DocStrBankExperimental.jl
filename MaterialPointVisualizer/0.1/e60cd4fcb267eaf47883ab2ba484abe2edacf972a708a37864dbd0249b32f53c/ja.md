```
vispts(coord, colormap::Symbol=:viridis, colorby::String="-1", attr::Vector=[-1], 
    psize::Float32=1f-2, sample_n::Int=1000000)
```

## 説明:

WGLMakieを使用してブラウザ/VSCodeで粒子を視覚化します。

  * coord: 粒子の座標。形状(n, m)の2Dまたは3D配列である必要があります。

ここで、nは粒子の数、mは次元(2または3)です。

  * colormap [オプション]: 視覚化に使用するカラーマップ。デフォルトは:viridisです。
  * colorby [オプション]: 粒子の色付けに使用する属性。デフォルトは"-1"で、これはz座標を意味します。attrが提供されている場合、それが代わりに使用されます。
  * attr [オプション]: 粒子の属性。長さnのベクトルである必要があります。
  * psize [オプション]: 視覚化における粒子のサイズ。デフォルトは1e-2です。
  * sample_n [オプション]: 視覚化のためにサンプリングする粒子の数。デフォルトは1,000,000です。この値を超える粒子の数がある場合、ランダムサンプルが取得されます。

## 例:

```julia
vispts(rand(10, 3))
vispts(rand(10, 3), colorby="random vals", attr=rand(10), psize=1f0, sample_n=5, colormap=:jet)
```
