```
λv,V=contour_beyn([eltype,] nep [,mintegrator];[tol,][logger,][σ,][radius,][linsolvercreator,][N,][neigs,][k])
```

The function computes eigenvalues using Beyn's contour integral approach, using an ellipse centered at `σ` with radii given in `radius`, or if only one `radius` is given, the contour is a circle. The numerical quadrature method is specified in `mintegrator`, which is a type inheriting from `MatrixIntegrator`, by default `MatrixTrapezoidal`. For a parallell implementation of the integrator use `MatrixTrapezoidalParallel`.  The integer `k` specifies size of the probe subspace. `N` corresponds to the number of quadrature points. Ellipses are the only supported contours. The `linsolvercreator` must create a linsolver that can handle (rectangular) matrices as right-hand sides, not only vectors. We integrate in complex arithmetic so `eltype` must be complex type.

The kwargs `neigs` specifies the number of wanted eigvals, and `k` is the number of columns in the matrix to be integrated (default `k=neigs+1`). If you give the `k` parameter and set `neigs=typemax(Int)` all found eigenvalues will be returned. The kwarg `sanity_check` decides if sorting and checking (and removal) of eigpairs should be done. If disabled, the method returns `k` (potentially inaccurate) eigpairs. The parameters `errmeasure` and `tol` and `rank_drop_tol` are used for the sanity check, to extract accurate eigenvalues.

# Example

```julia-repl
julia> using LinearAlgebra
julia> nep=nep_gallery("dep0");
julia> # Look for two eigvals in unit disk
julia> λv,V=contour_beyn(nep,radius=1.1,neigs=3);
julia> norm(compute_Mlincomb(nep,λv[1],V[:,1])) # Eigenpair 1
1.7462847531404259e-15
julia> norm(compute_Mlincomb(nep,λv[2],V[:,2])) # Eigenpair 2
7.69695692032292e-15
```

# References

  * Wolf-Jürgen Beyn, An integral method for solving nonlinear eigenvalue problems, Linear Algebra and its Applications 436 (2012) 3839–3863
