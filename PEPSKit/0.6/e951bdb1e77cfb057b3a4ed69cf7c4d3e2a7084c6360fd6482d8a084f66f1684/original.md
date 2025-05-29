```julia
struct SVDAdjoint{F, R}
```

Wrapper for a SVD algorithm `fwd_alg` with a defined reverse rule `rrule_alg`. If `isnothing(rrule_alg)`, Zygote differentiates the forward call automatically.

## Fields

  * `fwd_alg::Any`
  * `rrule_alg::Any`

## Constructors

```
SVDAdjoint(; kwargs...)
```

Construct a `SVDAdjoint` algorithm struct based on the following keyword arguments:

  * `fwd_alg::Union{Algorithm,NamedTuple}=(; alg::Symbol=sdd)`: SVD algorithm of the forward pass which can either be passed as an `Algorithm` instance or a `NamedTuple` where `alg` is one of the following:

      * `:sdd` : TensorKit's wrapper for LAPACK's `_gesdd`
      * `:svd` : TensorKit's wrapper for LAPACK's `_gesvd`
      * `:iterative` : Iterative SVD only computing the specifed number of singular values and vectors, see [`IterSVD`](@ref)
  * `rrule_alg::Union{Algorithm,NamedTuple}=(; alg::Symbol=full)`: Reverse-rule algorithm for differentiating the SVD. Can be supplied by an `Algorithm` instance directly or as a `NamedTuple` where `alg` is one of the following:

      * `:full`: Uses a modified version of TensorKit's reverse-rule for `tsvd` which doesn't solve any linear problem and instead requires access to the full SVD, see [`FullSVDReverseRule`](@ref).
      * `:gmres`: GMRES iterative linear solver, see the [KrylovKit docs](https://jutho.github.io/KrylovKit.jl/stable/man/algorithms/#KrylovKit.GMRES) for details
      * `:bicgstab`: BiCGStab iterative linear solver, see the [KrylovKit docs](https://jutho.github.io/KrylovKit.jl/stable/man/algorithms/#KrylovKit.BiCGStab) for details
      * `:arnoldi`: Arnoldi Krylov algorithm, see the [KrylovKit docs](https://jutho.github.io/KrylovKit.jl/stable/man/algorithms/#KrylovKit.Arnoldi) for details
