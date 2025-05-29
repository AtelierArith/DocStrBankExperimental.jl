```
sample!( pg::ParticleGroup{1,1}, α, k, σ, mesh::OneDGrid)
```

1D1V空間でのランドー減衰を初期化するために確率分布からサンプリングします。

$$
f_0(x,v,t) = \frac{n_0}{\sqrt{2π} v_{th}} ( 1 + \alpha cos(k_x x)) exp( - \frac{v^2}{2 v_{th}^2})
$$
