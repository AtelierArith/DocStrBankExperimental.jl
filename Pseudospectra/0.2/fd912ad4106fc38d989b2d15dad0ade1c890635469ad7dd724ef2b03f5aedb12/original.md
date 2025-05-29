```
psa_compute(T,npts,ax,eigA,opts,S=I) -> (Z,x,y,levels,info,Tproj,eigAproj,algo)
```

Compute pseudospectra of a (decomposed) matrix.

Uses a modified version of the code in [^Trefethen1999]. If the matrix `T` is upper triangular (e.g. from a Schur decomposition) the solver is much more efficient than otherwise.

# Arguments

  * `T`:      input matrix, usu. from `schur()`
  * `npts`:   grid will have `npts × npts` nodes
  * `ax`:     axis on which to plot `[min_real, max_real, min_imag, max_imag]`
  * `eigA`:   eigenvalues of the matrix, usu. also produced by `schur()`. Pass an empty vector if unknown.
  * `S`:    2nd matrix, if this is a generalized problem arising from an original rectangular matrix.
  * `opts`: a `Dict{Symbol,Any}` holding options. Keys used here are as follows:

| Key                 | Type           | Default           | Description                                                                                                                                                                        |
|:------------------- |:-------------- |:----------------- |:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `:levels`           | `Vector{Real}` | auto              | `log10(ϵ)` for the desired ϵ levels                                                                                                                                                |
| `:recompute_levels` | `Bool`         | true              | automatically recompute ϵ levels?                                                                                                                                                  |
| `:real_matrix`      | `Bool`         | `eltype(A)<:Real` | is the original matrix real? (Portrait is symmetric if so.) This is needed because `T` could be complex even if `A` was real.                                                      |
| `:proj_lev`         | `Real`         | ∞                 | The proportion by which to extend the axes in all directions before projection. If negative, exclude subspace of eigenvalues smaller than inverse fraction. ∞ means no projection. |
| `:scale_equal`      | `Bool`         | false             | force the grid to be isotropic?                                                                                                                                                    |
| `:threaded`         | `Bool`         | false             | distribute computation over Julia threads?                                                                                                                                         |

# Notes:

  * Projection is only done for square, dense matrices.  Projection for sparse matrices may be handled (outside this function) by a Krylov method which reduces the matrix to a projected Hessenberg form before invoking `psa_compute`.
  * This function does not compute generalized pseudospectra per se. They may be handled by pre- and post-processing.

# Outputs:

  * `Z`:         the singular values over the grid
  * `x`:         the x coordinates of the grid lines
  * `y`:         the y coordinates of the grid lines
  * `levels`:   the levels used for the contour plot (if automatically calculated)
  * `Tproj`:     the projected matrix (an alias to `T` if no projection was done)
  * `eigAproj`:  eigenvalues projected onto
  * `algo`: a Symbol indicating which algorithm was used
  * `info`:      flag indicating where automatic level creation fails:

| info | Meaning                                                                                   |
|:---- |:----------------------------------------------------------------------------------------- |
| 0    | No error                                                                                  |
| -1   | No levels in range specified (either manually, or if matrix is too normal to show levels) |
| -2   | Matrix is so non-normal that only zero singular values were found                         |
| -3   | Computation cancelled                                                                     |

[^Trefethen1999]: L.N.Trefethen, "Computation of pseudospectra," Acta Numerica 8, 247-295 (1999).
