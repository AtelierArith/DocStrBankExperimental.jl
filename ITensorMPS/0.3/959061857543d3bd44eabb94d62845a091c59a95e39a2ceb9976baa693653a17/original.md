```
contract(A::MPO, B::MPO; kwargs...) -> MPO
*(::MPO, ::MPO; kwargs...) -> MPO
```

Contract the `MPO` `A` with the `MPO` `B`, returning an `MPO` with the site indices that are not shared between `A` and `B`.

If you are contracting two MPOs with the same sets of indices, likely you want to call something like:

```julia
C = contract(A', B; cutoff=1e-12)
C = replaceprime(C, 2 => 1)
```

That is because if MPO `A` has the index structure `-s'-A-s-` and MPO `B` has the Index structure `-s'-B-s-`, if we only want to contract over on set of the indices, we would do `(-s'-A-s-)'-s'-B-s- = -s''-A-s'-s'-B-s- = -s''-C-s-`, and then map the prime levels back to pairs of primed and unprimed indices with: `replaceprime(-s''-C-s-, 2 => 1) = -s'-C-s-`.

Since this is a common use case, you can use the convenience function:

```julia
C = apply(A, B; cutoff=1e-12)
```

which is the same as the code above.

If you are contracting MPOs that have diverging norms, such as MPOs representing sums of local operators, the truncation can become numerically unstable (see https://arxiv.org/abs/1909.06341 for a more numerically stable alternative). For now, you can use the following options to contract MPOs like that:

```julia
C = contract(A, B; alg="naive", truncate=false)
# Bring the indices back to pairs of primed and unprimed
C = apply(A, B; alg="naive", truncate=false)
```

# Keywords

  * `cutoff::Float64=1e-14`: the cutoff value for truncating the density matrix  eigenvalues. Note that the default is somewhat arbitrary and subject to change,  in general you should set a `cutoff` value.
  * `maxdim::Int=maxlinkdim(A) * maxlinkdim(B))`: the maximal bond dimension of the results MPS.
  * `mindim::Int=1`: the minimal bond dimension of the resulting MPS.
  * `alg="zipup"`: Either `"zipup"` or `"naive"`. `"zipup"` contracts pairs of  site tensors and truncates with SVDs in a sweep across the sites, while `"naive"`  first contracts pairs of tensor exactly and then truncates at the end if `truncate=true`.
  * `truncate=true`: Enable or disable truncation. If `truncate=false`, ignore  other truncation parameters like `cutoff` and `maxdim`. This is most relevant  for the `"naive"` version, if you just want to contract the tensors pairwise  exactly. This can be useful if you are contracting MPOs that have diverging  norms, such as MPOs originating from sums of local operators.

See also [`apply`](@ref) for details about the arguments available.
