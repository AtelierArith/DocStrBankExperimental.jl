```
distance(M::AbstractManifold, p, q)
```

点 `p` と `q` の間の最短距離は、[`AbstractManifold`](@ref) `M` 上で次のように定義されます。

$$
d(p,q) = \inf_{γ} L(γ),
$$

ここで、infimum は、$γ(a)=p$ および $γ(b)=q$ を接続するすべての区分的滑らかな曲線 $γ: [a,b] \to \mathcal M$ にわたります。

$$
L(γ) = \displaystyle\int_{a}^{b} \lVert \dotγ(t)\rVert_{γ(t)} \mathrm{d}t
$$

は曲線 $γ$ の長さです。

もし $\mathcal M$ が連結でない場合、すなわち複数の非連結成分から構成される場合、異なる成分に属する2点間の距離は $∞$ であるべきです。
