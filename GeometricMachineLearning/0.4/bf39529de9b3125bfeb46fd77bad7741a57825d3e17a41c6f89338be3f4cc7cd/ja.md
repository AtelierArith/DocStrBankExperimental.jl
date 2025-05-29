```
SympNet <: NeuralNetworkIntegrator
```

`SympNet`型は[`GSympNet`](@ref)および[`LASympNet`](@ref)を包含します。SympNets [jin2020sympnets](@cite)は*標準的なシンプレクティックフロー*の普遍的近似器です。これは、次のマップに対して

$$
    \varphi:\mathbb{R}^{2n}\to\mathbb{R}^{2n} \text{ with } (\nabla\varphi)^T\mathbb{J}\nabla\varphi = \mathbb{J},
$$

任意の精度で$\varphi$を近似するSympNetを見つけることができることを意味します。
