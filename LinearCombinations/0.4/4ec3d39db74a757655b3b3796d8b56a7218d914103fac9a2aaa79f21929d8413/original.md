```
cat(t::AbstractTensor...) -> Tensor
```

Concatenate the tensors given as arguments. This function is multilinear.

See also [`flatten`](@ref).

# Example

```jldoctest
julia> LinearCombinations.cat(Tensor('x'), Tensor('y', Tensor('z', 'w')))
'x'⊗'y'⊗('z'⊗'w')
```
