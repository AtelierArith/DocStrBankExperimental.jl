Create energy spectrum plot. The energy at a scalar wavenumber level $\kappa \in \mathbb{N}$ is defined by

$$
\hat{e}(\kappa) = \int_{\kappa \leq \| k \|_2 < \kappa + 1} | \hat{e}(k) | \mathrm{d} k,
$$

as in San and Staples [San2012](@cite).

Keyword arguments:

  * `sloperange = [0.6, 0.9]`: Percentage (between 0 and 1) of x-axis where the slope is plotted.
  * `slopeoffset = 1.3`: How far above the energy spectrum the inertial slope is plotted.
  * `kwargs...`: They are passed to [`observespectrum`](@ref).
