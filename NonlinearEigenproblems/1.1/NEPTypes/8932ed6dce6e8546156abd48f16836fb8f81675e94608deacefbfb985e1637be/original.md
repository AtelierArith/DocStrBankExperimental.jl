```
struct SPMF_NEP{T<:AbstractMatrix,Ftype}  <: AbstractSPMF{T}
function SPMF_NEP(AA, fii [,check_consistency=true] [,Schur_fact = false]
                  [,align_sparsity_patterns = false] [,Ftype=ComplexF64])
```

An `SPMF_NEP` is a `NEP` defined by a *S*um of *P*roducts of *M*atrices and *F*unctions, i.e.,

$$
M(λ)=∑_i A_i f_i(λ).
$$

All of the matrices $A_0,...$ are of size $n×n$ and $f_i$ are a functions. The  functions $f_i$ must be defined for matrices in the standard matrix function sense. The constructor creates a `SPMF_NEP` consisting of matrices `AA` and functions `fii`.

# Parameters

  * `AA` is a `Vector` of matrices. The matrices have to be of the same type. If you need a NEP with different types you can use [`SumNEP`](@ref) to construct a sum of two `SPMF_NEP`.
  * `fii` is a `Vector` of functions. Each function takes one parameter `S`. The functions must be available both as a scalar valid function and a matrix function. If `S` is a square matrix, `fii[k](S)` musst also be a square matrix. If `S` is a scalar `fii[k](S)` is a scalar.
  * `check_consistency` (default `true`) determines if we should initiate by running tests to verify that the `fii` satisfies the conditions that every function is valid both for matrices and scalars. This is done by using `@code_typed` and the functions need to be type-stable in that sense.
  * `align_sparsity_patterns` (default `false`) has effect only for sparse matrices (`SparseMatrixCSC`). If `align_sparsity_patterns=true` the `SparseMatrixCSC` matrices will be replaced by equivalent `SparseMatrixCSC` matrices where the `colptr` and `rowval` are identical. This increases the speed of some functions, e.g., `compute_Mder`. If `align_sparsity_patterns=true` the matrices in the NEP should be considered read only. If the sparsity patterns are completely or mostly distinct, it may be more efficient to set this flag to false.
  * `Ftype` (default `ComplexF64`) determines an underlying type of the functions. The output of any function should be "smaller" than the promoted type of the input and `Ftype`. More precisely, if `F=fii[k]`, then the type logic is as follows `eltype(F(λ))=promote_type(eltype(λ),Ftype)`.
  * `Schur_fact` (default `false`) determines if the `compute_MM` function should triangularize the matrix before carrying out the computation. This can be faster for large matrices.

# Example

```julia-repl
julia> A0=[1 3; 4 5]; A1=[3 4; 5 6];
julia> id_op=S -> one(S) # Note: We use one(S) to be valid both for matrices and scalars
julia> exp_op=S -> exp(S)
julia> nep=SPMF_NEP([A0,A1],[id_op,exp_op]);
julia> compute_Mder(nep,1)-(A0+A1*exp(1))
2×2 Array{Float64,2}:
 0.0  0.0
 0.0  0.0
```
