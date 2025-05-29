```
force_layout(data::DataMatrix;
             ndim=3,
             k,
             adj,
             kprojection=10,
             obs=:copy,
             adj_out,
             niter = 100,
             link_distance = 4,
             link_strength = 2,
             charge = 5,
             charge_min_distance = 1,
             theta = 0.9,
             center_strength = 0.05,
             velocity_decay = 0.9,
             initialAlpha = 1.0,
             finalAlpha = 1e-3,
             initialScale = 10,
             seed,
             rng)
```

Compute the Force Layout (also known as a force directed knn-graph or SPRING plots) for `data`. Usually, `data` is a DataMatrix after reduction to `10-100` dimensions by `svd`.

A Force Layout is computed by running a physics simulation were the observations are connected by springs (such that connected observations are attracted), a general "charge" force repelling all observations from each other and a centering force that keep the observations around the origin. The implementation is based on d3-force: https://github.com/d3/d3-force, also see LICENSE.md.

Exactly one of the kwargs `k` and `adj` must be provided. See details below.

General parameters:

  * `k` - Number of nearest neighbors to connect each observation to (computes `adj` below).
  * `adj` - An sparse, symmetric, adjacency matrix with booleans. `true` if two observations are connected by a spring and `false` otherwise.
  * `kprojection` - The number of nearest neighbors used when projecting onto the resulting force layout. (Not used in the computation of the layout, only during projection.)
  * `obs` - Can be `:copy` (make a copy of source `obs`) or `:keep` (share the source `obs` object).
  * `adj_out` - Optional `Ref`. If specified, the (computed) `adj` matrix will be assigned to `adj_out`.

Paramters controlling the physics simulation:

  * `niter` - Number of iterations to run the simulation.
  * `link_distance` - The length of each spring.
  * `link_strength` - The strength of the spring force.
  * `charge` - The strength of the charge force.
  * `charge_min_distance` - Used to avoid numerical instabilities by limiting the charge force for observations that are very close.
  * `theta` - Parameter controlling accuracy in the Barnes-Hut approximation for charge forces.
  * `center_strength` - Strength of the centering force.
  * `velocity_decay` - At each iteration, the current velocity for an observations is multiplied by `velocity_decay`.
  * `initialAlpha` - The alpha value decreases over time and allows larger changes to happen early, while being more stable towards the end.
  * `finalAlpha` - See `initialAlpha`
  * `initialScale` - The simulation is initialized by randomly drawing each observation from a multivariate Gaussian, and is scaled by `initialScale`.
  * `seed` - Optional random seed used to init `rng`. NB: This requires the package `StableRNGs` to be loaded.
  * `rng` - Optional RNG object. Useful for reproducibility.

# Examples

```julia
julia> force_layout(data; ndim=3, k=100)
```
