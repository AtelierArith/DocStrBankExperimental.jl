```
SEstimator{L<:BoundedLossFunction} <: AbstractMEstimator
```

S-estimator for a given bounded loss function.

The S-estimator is obtained by minimizing the scale estimate:

$$
\hat{\mathbf{\beta}} = \underset{\mathbf{\beta}}{\textrm{argmin }} \hat{\sigma}^2
$$

where the robust scale estimate $\hat{\sigma}}$ is solution of:

$$
\dfrac{1}{n} \sum_{i=1}^n \rho\left(\dfrac{r_i}{\hat{\sigma}}\right) = \delta
$$

with the residuals  $\mathbf{r} = \mathbf{y} - \mathbf{X} \mathbf{\beta}$ , $\rho$ is a bounded loss function with  $\underset{r \to \infty}{\lim} \rho(r) = 1$ and $\delta$ is the finite breakdown point, usually 0.5.

# Fields

  * `loss`: the [`LossFunction`](@ref) used for the robust estimation.
