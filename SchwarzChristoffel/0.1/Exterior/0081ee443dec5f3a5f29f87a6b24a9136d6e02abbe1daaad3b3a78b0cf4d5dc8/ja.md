```
KarmanTrefftzMap(ν,ϵ,δ,C[;N = 200]) <: ConformalMap
```

単位円の外部からカーマン・トレフツ翼型の外部へのマップを作成します。

マッピングの形式は次の通りです。

$$
\frac{z-\nu C}{z+\nu C}  =
\left(\frac{\tilde{\zeta}-C}{\tilde{\zeta}+C}\right)^\nu
$$

ここで、$\tilde{\zeta}$は中間平面の座標であり、この平面では円の半径は$a$で、中心は$\epsilon C e^{i\delta}$にあります：

$$
\tilde{\zeta} = \epsilon C e^{i\delta} + a \zeta
$$

注意すべきは、$a/C \geq 1$であり、これは$\epsilon$と$\delta$の選択によって決まります。

後縁角$(2-\nu)\pi$は$\nu$によって指定されます。厚さは$\epsilon C \cos\delta$によって制御され、カンバーは$\epsilon C \sin\delta$によって制御されます。翼型の弦長は約$4C$です。一般に、$\epsilon$は1よりもはるかに小さく、$\delta$は$\pi/2$と$\pi$の間であるべきです。

得られたマップ`m`は、単一またはベクトルの点`ζ`で評価することができ、`m(ζ)`で使用します。

# 例

```jldoctest
julia> ν = 1.9; ϵ = 0.1; δ = π; C = 0.25;

julia> m = KarmanTrefftzMap(ν,ϵ,δ,C)
Karman-Trefftz map

julia> ζ = [1.0+3.0im,-2.0-2.0im,0.0+1.1im];

julia> m(ζ)
3-element Array{Complex{Float64},1}:
   0.268188+0.764722im
  -0.624265-0.502634im
 -0.0390996+0.126737im
```
