```
PoissonEquation(h, ensemble) ::GainEquation
```

Returns a Poisson equation struct representing the equation $\nabla\cdot(p\nabla \phi) = - \tilde h$, where $p$ is a probability density and $\tilde h = h-\int h p dx$.  The container contains the following fields

  * `:h':``h`` itself
  * `:positions': an i.i.d. sample from``p``, represented as a matrix
  * `:H': the evaluation of``h`` at the sample points
  * `:mean_H': the sample average of`H'
  * `:potential': the evaluation of``\phi`` at the sample points
  * `:gain': the evaluation of``K=\nabla \phi`` at the sample points

    solve!(eq::PoissonEquation, method::GainEstimationMethod)

Fills the field `:gain' with appropriate values. The fields`:H', `:mean_H', and`:potential' are stored to be re-used.

```
update!(eq::PoissonEquation, ensemble)
```

Fills the fields `:positions',`:H', and `:mean_H' according to the new samples from`ensemble'.

```
update!(eq::PoissonEquation)
```

Updates fields `:H', and`:mean_H' to be consistent with `:positions'.
