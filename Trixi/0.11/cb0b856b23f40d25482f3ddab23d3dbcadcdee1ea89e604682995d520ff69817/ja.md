```
enstrophy(u, gradients, equations::CompressibleNavierStokesDiffusion3D)
```

ノードごとのエンストロフィーを計算します。エンストロフィーは次のように定義されます。

$$
    \mathcal{E} = \frac{1}{2} \rho \boldsymbol{\omega} \cdot \boldsymbol{\omega}
$$

ここで、$\boldsymbol{\omega} = \nabla \times \boldsymbol{v}$ は [`vorticity`](@ref) です。3Dでは、$\boldsymbol{\omega}$ は完全な三成分ベクトルです。
