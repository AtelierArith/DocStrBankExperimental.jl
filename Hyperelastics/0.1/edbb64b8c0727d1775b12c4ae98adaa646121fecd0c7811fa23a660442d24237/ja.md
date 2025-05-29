```julia
MCC()

```

# モデル:

$$
W = \frac{1}{2}\zeta k T \sum\limits_{i=1}^{3}(\lambda_i^2-1)+\frac{1}{2}\mu k T\sum\limits_{i=1}^{3}[B_i+D_i-\log{(1+B_i)}-\log{(1+D_i)}]
$$

ここで:

$$
B_i = \frac{\kappa^2(\lambda_i^2-1)}{(\lambda_i^2+\kappa)^2}
$$

および

$$
D_i = \frac{\lambda_i^2 B_i}{\kappa}
$$

# パラメータ:

  * `ζkT`
  * `μkT`
  * `κ`

> Erman B, Monnerie L. Theory of elasticity of amorphous networks: effect of constraints along chains. Macromolecules. 1989 Aug;22(8):3342-8.

