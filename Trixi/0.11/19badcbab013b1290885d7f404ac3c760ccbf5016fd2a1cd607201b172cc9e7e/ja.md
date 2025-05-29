```
enstrophy(u, gradients, equations::CompressibleNavierStokesDiffusion2D)
```

ノードごとのエンストロフィーを計算します。定義は次の通りです。

$$
    \mathcal{E} = \frac{1}{2} \rho \omega \cdot \omega
$$

ここで、$\omega = \nabla \times \boldsymbol{v}$ は [`vorticity`](@ref) です。2Dでは、$\omega$ はスカラーに過ぎません。
