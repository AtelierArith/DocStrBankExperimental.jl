```
struct Trajectories{Dim}
```

A container for trajectory data of dimension `Dim`.

### Fields

  * `x0`: Initial coordinates, should be a matrix of size `Dim` x `n_traj`.
  * `xT`: Final coordinates, should be a matrix of size `Dim` x `n_traj`.

### Constructors

```
Trajectories(x0, xT)
```

Construct `Trajectories` directly from data.

```
Trajectories(dim, n_traj; corners = nothing, mu_sigma = nothing)
```

Construct `n_traj` random `Trajectories` of dimension `dim` for testing. 

The `x0` will lie inside the box defined by `corners = ((xmin, ymin, zmin, ...), (xmax, ymax, zmax, ...))` which  defaults to the unit box when not provided.

The `xT` are displaced from the `x0` by normal distributions along each dimension with means and variances defined by  `mu_sigma = [(mu1, sigma1), (mu2, sigma2), ...]`. If not provided, default to `mu = 1.0`, `sigma = 1.0`
