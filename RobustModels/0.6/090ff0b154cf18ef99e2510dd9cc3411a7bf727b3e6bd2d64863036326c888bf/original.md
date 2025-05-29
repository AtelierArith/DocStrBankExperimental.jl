```
MEstimator{L<:LossFunction} <: AbstractMEstimator
```

M-estimator for a given loss function.

The M-estimator is obtained by minimizing the loss function:

$$
\hat{\mathbf{\beta}} = \underset{\mathbf{\beta}}{\textrm{argmin}} \sum_{i=1}^n \rho\left(\dfrac{r_i}{\hat{\sigma}}\right)
$$

with the residuals  $\mathbf{r} = \mathbf{y} - \mathbf{X} \mathbf{\beta}$ , and a robust scale estimate $\hat{\sigma}$.

# Fields

  * `loss`: the [`LossFunction`](@ref) used for the robust estimation.
