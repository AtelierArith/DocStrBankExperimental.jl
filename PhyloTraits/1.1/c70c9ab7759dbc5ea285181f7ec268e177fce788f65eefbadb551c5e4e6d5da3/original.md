```
ParamsMultiBM <: ParamsProcess
```

Type for a multivariate Brownian diffusion (MBD) process on a network. Fields are `mu` (expectation), `sigma` (covariance matrix), `randomRoot` (whether the root is random, default to `false`), `varRoot` (if the root is random, the covariance matrix of the root, default to `[NaN]`), `shift` (a ShiftNet type, default to `missing`), and `L` (the lower triangular of the cholesky decomposition of `sigma`, computed automatically)

# examples and constructors

```jldoctest
julia> ParamsMultiBM([1.0, -0.5], [2.0 0.3; 0.3 1.0]) # no shifts
ParamsMultiBM:
Parameters of a MBD with fixed root:
mu: [1.0, -0.5]
Sigma: [2.0 0.3; 0.3 1.0]

julia> net = readnewick("((A:1,B:1):1,C:2);");

julia> shifts = ShiftNet(net.node[2], [-1.0, 2.0], net);

julia> ParamsMultiBM([1.0, -0.5], [2.0 0.3; 0.3 1.0], shifts) # with shifts
ParamsMultiBM:
Parameters of a MBD with fixed root:
mu: [1.0, -0.5]
Sigma: [2.0 0.3; 0.3 1.0]

There are 2 shifts on the network:
───────────────────────────────────────────
  Edge Number  Shift Value 1  Shift Value 2
───────────────────────────────────────────
          2.0           -1.0            2.0
───────────────────────────────────────────

```
