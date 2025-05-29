```Julia
BilinearExponential(loc, scl, shp, skw)
BilinearExponential(p::AbstractVector)
struct BilinearExponential{T<:Real} <: ContinuousUnivariateDistribution
    A::T
    loc::T
    scl::T
    shp::T
    skw::T
end
```

地質年代学で見られるさまざまな非対称確率分布を近似するために使用できる五つのパラメータを持つ擬似分布です（ベイズ的噴火年推定の結果として含まれます）。

この「バイリニア指数」分布は、その名前が示唆するように、二つの対数線形セグメントを持つ指数関数として定義され、アークタンジェントシグモイドによって結合されています：

$$
ℯ^{A} * ℯ^{v*xₛ*shp*skw - (1-v)*xₛ*shp/skw}
$$

ここで

$$
v = 1/2 - atan(xₛ)/π
$$

はシグモイドであり、左側で正の値を持ち、

$$
xₛ = (x - loc)/scl
$$

は位置パラメータ `loc` とスケールパラメータ `scl` でスケーリングされた `x` です。スケールパラメータ `scl` に加えて、追加の形状パラメータ `shp` と `skw` （それぞれ結果の分布の鋭さと歪みを制御します）は、すべて非負である必要があります。

もし四つのパラメータ `(loc, scl, shp, skw)` のみが指定された場合、正規化定数 `A` は、結果の分布が正規化されるように計算されます。
