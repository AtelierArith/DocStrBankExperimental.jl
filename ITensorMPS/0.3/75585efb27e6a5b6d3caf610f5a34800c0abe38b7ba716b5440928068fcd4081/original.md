```
contract(ψ::MPS, A::MPO; kwargs...) -> MPS
*(::MPS, ::MPO; kwargs...) -> MPS

contract(A::MPO, ψ::MPS; kwargs...) -> MPS
*(::MPO, ::MPS; kwargs...) -> MPS
```

Contract the `MPO` `A` with the `MPS` `ψ`, returning an `MPS` with the unique site indices of the `MPO`.

For example, for an MPO with site indices with prime levels of 1 and 0, such as `-s'-A-s-`, and an MPS with site indices with prime levels of 0, such as `-s-x`, the result is an MPS `y` with site indices with prime levels of 1, `-s'-y = -s'-A-s-x`.

Since it is common to contract an MPO with prime levels of 1 and 0 with an MPS with prime level of 0 and want a resulting MPS with prime levels of 0, we provide a convenience function `apply`:

```julia
apply(A, x; kwargs...) = replaceprime(contract(A, x; kwargs...), 2 => 1)`.
```

Choose the method with the `method` keyword, for example `"densitymatrix"` and `"naive"`.

# Keywords

  * `cutoff::Float64=1e-13`: the cutoff value for truncating the density matrix  eigenvalues. Note that the default is somewhat arbitrary and subject to  change, in general you should set a `cutoff` value.
  * `maxdim::Int=maxlinkdim(A) * maxlinkdim(ψ))`: the maximal bond dimension of the results MPS.
  * `mindim::Int=1`: the minimal bond dimension of the resulting MPS.
  * `normalize::Bool=false`: whether or not to normalize the resulting MPS.
  * `method::String="densitymatrix"`: the algorithm to use for the contraction.  Currently the options are "densitymatrix", where the network formed by the  MPO and MPS is squared and contracted down to a density matrix which is  diagonalized iteratively at each site, and "naive", where the MPO and MPS  tensor are contracted exactly at each site and then a truncation of the  resulting MPS is performed.

See also [`apply`](@ref).
