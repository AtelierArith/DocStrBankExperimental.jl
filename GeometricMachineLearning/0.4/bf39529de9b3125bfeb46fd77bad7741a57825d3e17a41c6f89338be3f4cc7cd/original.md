```
SympNet <: NeuralNetworkIntegrator
```

The `SympNet` type encompasses [`GSympNet`](@ref)s and [`LASympNet`](@ref)s.  SympNets [jin2020sympnets](@cite) are universal approximators of *canonical symplectic flows*. This means that for every map 

$$
    \varphi:\mathbb{R}^{2n}\to\mathbb{R}^{2n} \text{ with } (\nabla\varphi)^T\mathbb{J}\nabla\varphi = \mathbb{J},
$$

we can find a SympNet that approximates $\varphi$ arbitrarily well.
