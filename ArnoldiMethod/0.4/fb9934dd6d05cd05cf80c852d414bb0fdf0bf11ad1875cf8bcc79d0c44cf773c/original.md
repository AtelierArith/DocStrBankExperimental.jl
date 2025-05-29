```julia
partialschur(A; v1, workspace, nev, which, tol, mindim, maxdim, restarts) → PartialSchur, History
```

Find `nev` approximate eigenpairs of `A` with eigenvalues near a specified target.

The matrix `A` can be any linear map that implements `mul!(y, A, x)`, `eltype` and `size`.

The method will run iteratively until the eigenpairs are approximated to the prescribed tolerance or until `restarts` restarts have passed.

## Arguments

The most important keyword arguments:

| Keyword | Type                 | Default              | Description                                          |
| -------:|:-------------------- |:-------------------- |:---------------------------------------------------- |
|   `nev` | `Int`                | `min(6, size(A, 1))` | Number of eigenvalues                                |
| `which` | `Symbol` or `Target` | `:LM`                | One of `:LM`, `:LR`, `:SR`, `:LI`, `:SI`, see below. |
|   `tol` | `Real`               | `√eps`               | Tolerance for convergence: ‖Ax - xλ‖₂ < tol * ‖λ‖    |
|    `v1` | `AbstractVector`     | `nothing`            | Optional starting vector for the Krylov subspace     |

Regarding the initial vector `v1`: it will not be mutated, and it does not have to be normalized.

The target `which` can be any of:

|          Target | Description                                    |
| ---------------:|:---------------------------------------------- |
| `:LM` or `LM()` | Largest magnitude: `abs(λ)` is largest         |
| `:LR` or `LR()` | Largest real part: `real(λ)` is largest        |
| `:SR` or `SR()` | Smallest real part: `real(λ)` is smallest      |
| `:LI` or `LI()` | Largest imaginary part: `imag(λ)` is largest   |
| `:SI` or `SI()` | Smallest imaginary part: `imag(λ)` is smallest |

Note that as of ArnoldiMethod v0.4, you have to import `using ArnoldiMethod: LM` explicitly if you do not want to use symbols.

!!! note
    The targets `:LI` and `:SI` only make sense in complex arithmetic. In real arithmetic `λ` is an eigenvalue iff `conj(λ)` is an eigenvalue and this  conjugate pair converges simultaneously.


## Return values

The function returns a tuple

```julia
decomp, history = partialschur(A, ...)
```

where `decomp` is a [`PartialSchur`](@ref) struct which  forms a partial Schur decomposition of `A` to a prescribed tolerance:

```julia
> norm(A * decomp.Q - decomp.Q * decomp.R)
```

`history` is a [`History`](@ref) struct that holds some basic information about convergence of the method:

```julia
> history.converged
true
> @show history
Converged after 359 matrix-vector products
```

## Advanced usage

Further there are advanced keyword arguments for tuning the algorithm:

|    Keyword | Type  | Default                         | Description                      |
| ----------:|:----- |:------------------------------- |:-------------------------------- |
|   `mindim` | `Int` | `min(max(10, nev), size(A,1))`  | Minimum Krylov dimension (≥ nev) |
|   `maxdim` | `Int` | `min(max(20, 2nev), size(A,1))` | Maximum Krylov dimension (≥ min) |
| `restarts` | `Int` | `200`                           | Maximum number of restarts       |

When the algorithm does not converge, one can increase `restarts`. When the  algorithm converges too slowly, one can play with `mindim` and `maxdim`. It is  suggested to keep `mindim` equal to or slightly larger than `nev`, and `maxdim` is usually about two times `mindim`.
