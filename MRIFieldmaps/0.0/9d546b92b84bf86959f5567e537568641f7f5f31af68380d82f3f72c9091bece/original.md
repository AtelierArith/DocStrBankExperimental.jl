```
(fhat, times, out) = b0map(ydata, echotime; kwargs...)
```

Field map estimation from multiple (`ne ≥ 2`) echo-time images, using preconditioned nonlinear CG (NCG) with a monotonic line search. This code works with images of arbitrary dimensions (2D, 3D, etc.), and with multiple coils.

Caution: single coil data must be reshaped to size `(dims..., 1, ne)`.

The cost function for the single-coil case is: `cost(w) = ∑_{j=1}^{#voxel} ∑_{m=1}^ne ∑_{n=1}^ne     |y_{mj} y_{nj}| wj (1 - cos(w_j * (t_m - t_n) + ∠y_{ni} - ∠y_{mj})) + R(w)` where `t_n` denotes the echo time of the `n`th scan and `R(w) = 0.5 * | C * w |^2` is a quadratic roughness regularizer based on 1st-order or 2nd-order finite differences. See the documentation for the general multi-coil case.

The initial field map `finit` and output `fhat` are field maps in Hz, but internally the code works with `ω = 2π f` (rad/s).

# In

  * `ydata (dims..., nc, ne)` `ne` sets of complex images for `nc ≥ 1` coils
  * `echotime::Echotime (ne ≥ 2)` echo time offsets (in seconds)

# Options

  * `finit (dims)` initial fieldmap estimate (in Hz); default from `b0init()`
  * `smap (dims..., nc)` complex coil maps; default `nothing`
  * `mask (dims...)` logical reconstruction mask; default: `trues(size(finit))`
  * `ninner` # of inner iterations for monotonic line search default: `3` inner iterations
  * `b0init_args::NamedTuple = (;)` options for `b0init`, such as `threshold`
  * `niter` # of outer iterations (def: `30`)
  * `order` order of the finite-difference matrix (def: `2`)
  * `l2b` `log2` of regularization parameter (def: `-6`)
  * `gamma_type` CG direction:

      * `:PR` = Polak-Ribiere (default)
      * `:FR` = Fletcher-Reeves
  * `precon` Preconditioner:

      * `:I` (nothing)
      * `:diag`
      * `:chol` may require too much memory
      * `:ichol` (default)
  * `reset` # of iterations before resetting direction (def: `Inf`)
  * `df` Δf values in water-fat imaging (def: `[0]`) units Hz, e.g., `[440]` at 3T
  * `relamp` relative amplitudes in multi-peak water-fat (def: `[1]`)
  * `lldl_args::NamedTuple` options for `lldl`, default: `(;memory=2)`
  * `track::Bool` if `true` then track cost and save all iterations (def: `false`)
  * `chat::Bool = true` # `@info` updates each iteration
  * `chat_iter::Int = 10` # print progress report every few iterations.

# Out

  * `fhat` final fieldmap estimate in Hz
  * `times (niter+1)` wall time for each iteration
  * `out::NamedTuple` that contains:

      * `(xw, xf) (dims)` water / fat images if `!iszero(df)`
      * `finit (dims)` initial fieldmap
  * if `track == true` then `out` also contains:

      * `costs (niter+1)` (nonconvex) cost for each iteration
      * `fhats (dims, niter+1)` fieldmap estimates every iteration

The algorithm is based on the paper: C Y Lin, J A Fessler, "Efficient Regularized Field Map Estimation in 3D MRI", IEEE TCI 2020 https://doi.org/10.1109/TCI.2020.3031082 https://arxiv.org/abs/2005.08661

Please cite that paper if you use this code.
