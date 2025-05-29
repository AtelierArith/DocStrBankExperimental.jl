`(Ω, weights) = window_quadrature_weights(pts::Vector{Float64}, g; kwargs...)`

Computes the weights {α*j}*{j=1}^n such that

H_{α}(ω) ≈ G(ω)

for |ω| ≤ Ω. The default Ω is chosen to be 90% of the continuous Nyquist frequency, which is n/(4*(b-a)). In the case where Ω = O(n), with the current routine this computation will scale like O(n³). If Ω is fixed and doesn't grow with n, then it will scale like O(n log n).

The object `g::G` can be any structure represnting a window function. It needs to implement the methods described at the top of `./src/window.jl`.

Keyword arguments are as follows:

  * `solver = default_solver(pts)`: the numerical method used to obtain the

weights. See the paper for full details, but this is a potentially very large least squares problem with a rank-deficient design matrix that needs to be solved. Options are:

  * `KrylovSolver(::KrylovPreconditioner, pre_kernel::Type{K}, perturbation::Float64)`:  the default which uses `Krylov.lsmr` to compute the weights in an entirely matrix-free way. The `::KrylovPreconditioner` object is crucial for this to be accurate.  For small data sizes (maybe n ~ 5k or lower), the default `CholeskyPreconditioner()`  is your best option. But for larger data sizes, considering `]add`-ing `HMatrices.jl` and using the `HMatrixPreconditioner(atol, lu_atol)`, which will scale *much* better. The second argument, `pre_kernel`, is a *type* that that is an internal detail in assembling the preconditioned linear system.  In general, we suggest using `SincKernel` in 1D, and `KaiserKernel` in 2+D. Finally, `perturbation` is another interal detail in the preconditioned linear system. A higher value will make certain preconditioners more stable, but slow down convergence. We suggest a default choice of `1e-8`. See the example files for a demo of using a custom `KrylovSolver`.
  * `DenseSolver()`: uses a simple `qr(F, ColumnNorm())` on the nonuniform Fourier matrix.  This will almost never be the fastest option, but we offer it for those who are exploring or debugging.
  * `SketchSolver()`: this is an extension that requires `LowRankApprox.jl`. In the setting where `Ω` is small or fixed and you are going to crank `n` up, the Fourier matrix has a bounded rank and using the NUFFT and sketching methods one can obtain weights rapidly with a partial QR. This may or may not be faster than the `KrylovSolver` with a good preconditioner, and the  circumstance where you should reach for this one is probably rare.
  * `Ω = default_Ω(pts, g)`: the highest frequency that the weights will attempt

to resolve. This defaults to 80% of the Nyquist frequency for most windows, but   can be adaptively reduced if the norm of the weights is too high. See options below.   Note that in D dimensions for D > 1, `Ω` is/must be a D-tuple.

  * `max_wt_norm = Inf`: the maximum permissible norm of the weight vector. This norm has a big impact on the size of the aliasing bias, so it can sometimes be advantageous to reduce `Ω` in exchange for a smaller norm. If this is set to a finite value and the computed weights exceed it, then `Ω` is reduced as `Ω .*= reduction_factor` and the weights are recomputed.
  * `reduction_factor = 0.9`: this quantity determines how aggressively we shrink `Ω` in the case when the computed weights exceed `max_wt_norm`. Making it larger may save you on the cost of recomputing weights, but it may mean your ultimate `Ω` is lower than it could have been.
  * `verbose = true`: whether or not to print output.
