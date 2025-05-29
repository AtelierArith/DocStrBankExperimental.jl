```
apply(A::RotationAroundAxisAction, θ, p)
```

点 `p` を [`Euclidean(3)`](@ref) 多様体上で軸 `A.axis` の周りに角度 `θ` だけ回転させます。式は次のようになります。

$$
p_{rot} = (\cos(θ))p + (k×p) \sin(θ) + k (k⋅p) (1-\cos(θ)),
$$

ここで $k$ はベクトル `A.axis` であり、`⋅` はドット積です。
