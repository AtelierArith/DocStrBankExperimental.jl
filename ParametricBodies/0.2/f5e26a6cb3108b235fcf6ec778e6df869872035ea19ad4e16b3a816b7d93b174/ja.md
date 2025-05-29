```
HashedLocator

- `refine<:Function`` 有界ニュートン根探索ステップを実行します
- `lims::NTuple{2,T}:` `uv` パラメータの制限
- `hash<:AbstractArray{T,2}:` `refine` に良い初期条件を供給するためのハッシュ
- `lower::SVector{2,T}:` ξ空間におけるハッシュの下隅
- `step::T:` ハッシュのξ解像度
```

パラメトリック曲線上で効率的かつ比較的安定した `locate` を実行するためのタイプ。ニュートン法は速いですが、一般的なパラメトリック曲線に対しては非常に不安定になる可能性があります。これは、`hash` を補間して近い初期 `uv` 推測を供給し、ニュートンの `refine` で導関数の調整を制限することで軽減されます。

---

```
HashedLocator(curve,lims;t⁰=0,step=1,buffer=2,T=Float32,mem=Array)
```

曲線をサンプリングしてバウンディングボックスを見つけることによって HashedLocator を作成します。このボックスは `buffer` の量だけ拡張されます。ハッシュ配列はボックスを解像度 `step` でスパンするように割り当てられ、`update!(::,curve,t⁰,samples)` を使用して初期化されます。

例:

```
t = 0.
curve(θ,t) = SA[cos(θ+t),sin(θ+t)]
locator = HashedLocator(curve,(0.,2π),t⁰=t,step=0.25)
@test isapprox(locator(SA[.3,.4],t),atan(4,3),rtol=1e-4)
@test isapprox(curve(locator(SA[-1.2,.9],t),t),SA[-4/5,3/5],rtol=1e-4)

body = ParametricBody(curve,locator)
@test isapprox(sdf(body,SA[-.3,-.4],t),-0.5,rtol=1e-4) # ハッシュ内
@test isapprox(sdf(body,SA[-3.,-4.],t), 4.0,rtol=2e-2) # ハッシュ外
```
