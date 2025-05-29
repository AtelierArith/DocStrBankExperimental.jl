```
n_body_basis(
n::Integer,
n_parties::Integer;
sb::AbstractVector{<:AbstractMatrix} = [pauli(1), pauli(2), pauli(3)],
eye::AbstractMatrix = I(size(sb[1], 1))
```

Return the basis of `n` nontrivial operators acting on `n_parties`, by default using sparse Pauli matrices.

For example, `n_body_basis(2, 3)` generates all products of two Paulis and one identity, so ${X ⊗ X ⊗ 1, X ⊗ 1 ⊗ X, ..., X ⊗ Y ⊗ 1, ..., 1 ⊗ Z ⊗ Z}$.

Instead of Paulis, a basis can be provided by the parameter `sb`, and the identity can be changed with `eye`.

This function returns a generator, which can then be used e.g. in for loops without fully allocating the entire basis at once. If you need a vector, call `collect` on it.
