```
convert2affinePCE(mu::Real, sigma::Real, op::AbstractCanonicalOrthoPoly; kind::String)
```

アフィンPCE係数$x_0$と$x_1$を次の式から計算します。

$$
X = a_1 + a_2 \Xi = x_0 + x_1 \phi_1(\Xi),
$$

ここで、$\phi_1(t) = t-\alpha_0$は一次モニック基底多項式です。

AbstractCanonicalOrthoPolyのサブタイプで動作します。キーワード`kind in ["lbub", "μσ"]`は、`p1`と`p2`が下限/上限または平均/標準偏差の意味を持つかどうかを指定します。 ```
