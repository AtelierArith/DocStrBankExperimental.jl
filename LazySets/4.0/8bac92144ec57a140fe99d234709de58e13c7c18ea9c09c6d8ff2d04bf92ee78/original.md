# Extended help

```
σ(d::AbstractVector, B::AbstractBallp)
```

### Algorithm

The support vector of the unit ball in the $p$-norm along direction $d$ is:

$$
σ(d, \mathcal{B}_p^n(0, 1)) = \dfrac{\tilde{v}}{‖\tilde{v}‖_q},
$$

where $\tilde{v}_i = \frac{|d_i|^q}{d_i}$ if $d_i ≠ 0$ and $\tilde{v}_i = 0$ otherwise, for all $i=1,…,n$, and $q$ is the conjugate number of $p$. By the affine transformation $x = r\tilde{x} + c$, one obtains that the support vector of $\mathcal{B}_p^n(c, r)$ is

$$
σ(d, \mathcal{B}_p^n(c, r)) = \dfrac{v}{‖v‖_q},
$$

where $v_i = c_i + r\frac{|d_i|^q}{d_i}$ if $d_i ≠ 0$ and $v_i = 0$ otherwise, for all $i = 1, …, n$.

If the direction has norm zero, the center of the ball is returned.
