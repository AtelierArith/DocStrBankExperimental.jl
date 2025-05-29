```
contour_block_SS([eltype,] nep [,mintegrator];[tol,][logger,][σ,][radius,][linsolvercreator,][N,][neigs,][k,][L])
```

This is an implementation of the block_SS contour integral method which is based on the computation of higher order moments. The contour is an ellipse centered at `σ` with radii given in `radius`, or if only one `radius` is given, the contour is a circle. The numerical quadrature method is specified in `mintegrator`, which is a type inheriting from `MatrixIntegrator`, by default `MatrixTrapezoidal`. For a parallell implementation of the integrator use `MatrixTrapezoidalParallel`.  The integer `k` specifies size of the probe subspace. `N` corresponds to the number of quadrature points. The integer L specifies the number of moments. Ellipses are the only supported contours. The `linsolvercreator` must create a linsolver that can handle (rectangular) matrices as right-hand sides, not only vectors. We integrate in complex arithmetic so `eltype` must be complex type.

# Example

```julia-repl
julia> nep=SPMF_NEP([[0 1 ; 1 1.0], [1 0 ; 0 0]], [s->one(s),s->exp(1im*s^2)]);
julia> λ,V=contour_assu(nep,radius=3,neigs=6)
julia> @show λ
6-element Array{Complex{Float64},1}:
  4.496403249731884e-15 + 2.506628274630998im
        -2.506628274631 - 2.8727020762175925e-15im
  3.219972424519104e-16 - 2.5066282746310034im
     2.5066282746310096 - 1.1438072192922029e-15im
 -2.3814273710772784e-7 - 7.748469160458366e-8im
   2.381427350935646e-7 + 7.748467479992284e-8im
```

# References

  * Asakura, Sakurai, Tadano, Ikegami, Kimura, A numerical method for nonlinear eigenvalue problems using contour integrals, JSIAM Letters, 2009 Volume 1 Pages 52-55
  * Van Beeumen,  Meerbergen, Michiels. Connections between contour integration and rational Krylov methods for eigenvalue problems, 2016, TW673, https://lirias.kuleuven.be/retrieve/415487/
