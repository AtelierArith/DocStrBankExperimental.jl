```
BasisSetRepresentation(
    hamiltonian::AbstractHamiltonian, addr=starting_address(hamiltonian);
    sizelim=10^7, cutoff, filter, max_depth, minimum_size, sort=false, kwargs...
)
BasisSetRepresentation(hamiltonian::AbstractHamiltonian, addresses::AbstractVector; kwargs...)
```

Eagerly construct the basis set representation of the operator `hamiltonian` with all addresses reachable from `addr`. Instead of a single address, a vector of `addresses` can be passed.

An `ArgumentError` is thrown if `dimension(hamiltonian) > sizelim` in order to prevent memory overflow. Set `sizelim = Inf` in order to disable this behaviour.

Providing the number `nnzs` of expected calculated matrix elements and `col_hint` for the estimated number of nonzero off-diagonal matrix elements in each matrix column may improve performance.

Providing an energy cutoff will skip the columns and rows with diagonal elements greater than `cutoff`. Alternatively, an arbitrary `filter` function can be used instead. Addresses passed as arguments are not filtered. To generate the matrix truncated to the subspace spanned by the `addresses`, use `filter = Returns(false)`.

Providing a `max_depth` will limit the size of the matrix and basis by only visiting addresses that are connected to the `starting_address` through `max_depth` hops through the Hamiltonian. Similarly, providing `minimum_size` will stop the bulding process after the basis reaches a length of at least `minimum_size`.

Setting `sort` to `true` will sort the matrix rows and columns. This is useful when the order of the columns matters, e.g. when comparing matrices. Any additional keyword arguments are passed on to `Base.sortperm`.

!!! warning
    ```
    The order of the returned basis and matrix rows and columns is arbitrary and
    non-deterministic. Use `sort=true` if the ordering matters.
    ```


## Fields

  * `sparse_matrix`: sparse matrix representing `hamiltonian` in the basis `basis`
  * `basis`: vector of addresses
  * `hamiltonian`: the Hamiltonian `hamiltonian`

## Example

```jldoctest; filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2***"
julia> hamiltonian = HubbardReal1D(BoseFS(1,0,0));

julia> bsr = BasisSetRepresentation(hamiltonian)
BasisSetRepresentation(HubbardReal1D(fs"|1 0 0⟩"; u=1.0, t=1.0)) with dimension 3 and 6 stored entries:3×3 SparseArrays.SparseMatrixCSC{Float64, Int32} with 6 stored entries:
   ⋅   -1.0  -1.0
 -1.0    ⋅   -1.0
 -1.0  -1.0    ⋅

julia> BasisSetRepresentation(hamiltonian, bsr.basis[1:2]; filter = Returns(false)) # passing addresses and truncating
BasisSetRepresentation(HubbardReal1D(fs"|1 0 0⟩"; u=1.0, t=1.0)) with dimension 2 and 2 stored entries:2×2 SparseArrays.SparseMatrixCSC{Float64, Int32} with 2 stored entries:
   ⋅   -1.0
 -1.0    ⋅

julia> using LinearAlgebra; round.(eigvals(Matrix(bsr)); digits = 4) # eigenvalues
3-element Vector{Float64}:
 -2.0
  1.0
  1.0

julia> ev = eigvecs(Matrix(bsr))[:,1]; ev = ev .* sign(ev[1]) # ground state eigenvector
3-element Vector{Float64}:
 0.5773502691896257
 0.5773502691896255
 0.5773502691896257

julia> dv = DVec(zip(bsr.basis, ev)) # ground state as DVec
DVec{BoseFS{1, 3, BitString{3, 1, UInt8}},Float64} with 3 entries, style = IsDeterministic{Float64}()
  fs"|0 0 1⟩" => 0.57735
  fs"|0 1 0⟩" => 0.57735
  fs"|1 0 0⟩" => 0.57735
```

Has methods for [`dimension`](@ref), [`sparse`](@ref), [`Matrix`](@ref), [`starting_address`](@ref).

Part of the [`AbstractHamiltonian`](@ref) interface. See also [`build_basis`](@ref).
