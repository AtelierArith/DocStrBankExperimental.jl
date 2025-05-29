```
dmrg(H::MPO, psi0::MPS; kwargs...)
dmrg(H::MPO, psi0::MPS, sweeps::Sweeps; kwargs...)
```

Use the density matrix renormalization group (DMRG) algorithm to optimize a matrix product state (MPS) such that it is the eigenvector of lowest eigenvalue of a Hermitian matrix `H`, represented as a matrix product operator (MPO).

```
dmrg(Hs::Vector{MPO}, psi0::MPS; kwargs...)
dmrg(Hs::Vector{MPO}, psi0::MPS, sweeps::Sweeps; kwargs...)
```

Use the density matrix renormalization group (DMRG) algorithm to optimize a matrix product state (MPS) such that it is the eigenvector of lowest eigenvalue of a Hermitian matrix `H`. This version of `dmrg` accepts a representation of H as a Vector of MPOs, `Hs = [H1, H2, H3, ...]` such that `H` is defined `as H = H1 + H2 + H3 + ...` Note that this sum of MPOs is not actually computed; rather the set of MPOs `[H1,H2,H3,..]` is efficiently looped over at each step of the DMRG algorithm when optimizing the MPS.

```
dmrg(H::MPO, Ms::Vector{MPS}, psi0::MPS; weight=1.0, kwargs...)
dmrg(H::MPO, Ms::Vector{MPS}, psi0::MPS, sweeps::Sweeps; weight=1.0, kwargs...)
```

Use the density matrix renormalization group (DMRG) algorithm to optimize a matrix product state (MPS) such that it is the eigenvector of lowest eigenvalue of a Hermitian matrix `H`, subject to the constraint that the MPS is orthogonal to each of the MPS provided in the Vector `Ms`. The orthogonality constraint is approximately enforced by adding to `H` terms of the form `w|M1><M1| + w|M2><M2| + ...` where `Ms=[M1, M2, ...]` and `w` is the "weight" parameter, which can be adjusted through the optional `weight` keyword argument.

!!! note
    `dmrg` will report the energy of the operator `H + w|M1><M1| + w|M2><M2| + ...`, not the operator `H`. If you want the expectation value of the MPS eigenstate with respect to just `H`, you can compute it yourself with an observer or after DMRG is run with `inner(psi', H, psi)`.


The MPS `psi0` is used to initialize the MPS to be optimized.

The number of sweeps of thd DMRG algorithm is controlled by passing the `nsweeps` keyword argument. The keyword arguments `maxdim`, `cutoff`, `noise`, and `mindim` can also be passed to control the cost versus accuracy of the algorithm - see below for details.

Alternatively the number of sweeps and accuracy parameters can be passed through a `Sweeps` object, though this interface is no longer preferred.

Returns:

  * `energy::Number` - eigenvalue of the optimized MPS
  * `psi::MPS` - optimized MPS

Keyword arguments:

  * `nsweeps::Int` - number of "sweeps" of DMRG to perform

Optional keyword arguments:

  * `maxdim` - integer or array of integers specifying the maximum size  allowed for the bond dimension or rank of the MPS being optimized.
  * `cutoff` - float or array of floats specifying the truncation error cutoff  or threshold to use for truncating the bond dimension or rank of the MPS.
  * `eigsolve_krylovdim::Int = 3` - maximum dimension of Krylov space used to  locally solve the eigenvalue problem. Try setting to a higher value if  convergence is slow or the Hamiltonian is close to a critical point. [^krylovkit]
  * `eigsolve_tol::Number = 1e-14` - Krylov eigensolver tolerance. [^krylovkit]
  * `eigsolve_maxiter::Int = 1` - number of times the Krylov subspace can be  rebuilt. [^krylovkit]
  * `eigsolve_verbosity::Int = 0` - verbosity level of the Krylov solver.  Warning: enabling this will lead to a lot of outputs to the terminal. [^krylovkit]
  * `ishermitian=true` - boolean specifying if dmrg should assume the MPO (or more  general linear operator) represents a Hermitian matrix. [^krylovkit]
  * `noise` - float or array of floats specifying strength of the "noise term"  to use to aid convergence.
  * `mindim` - integer or array of integers specifying the minimum size of the  bond dimension or rank, if possible.
  * `outputlevel::Int = 1` - larger outputlevel values make DMRG print more  information and 0 means no output.
  * `observer` - object implementing the [Observer](@ref observer) interface  which can perform measurements and stop DMRG early.
  * `write_when_maxdim_exceeds::Int` - when the allowed maxdim exceeds this  value, begin saving tensors to disk to free RAM memory in large calculations
  * `write_path::String = tempdir()` - path to use to save files to disk  (to save RAM) when maxdim exceeds the `write_when_maxdim_exceeds` option, if set

[^krylovkit]: The `dmrg` function in `ITensorMPS.jl` currently uses the `eigsolve` function in `KrylovKit.jl` as the internal the eigensolver. See the `KrylovKit.jl` documention on the `eigsolve` function for more details: [KrylovKit.eigsolve](https://jutho.github.io/KrylovKit.jl/stable/man/eig/#KrylovKit.eigsolve).
