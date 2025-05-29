```
flatten(t::AbstractTensor) -> Tensor
flatten(a::AbstractLinear{<:AbstractTensor}) -> AbstractLinear{Tensor}
```

Recursively take all tensor components and concatenate the result. This function is linear.

See also [`cat`](@ref).

# Example

```jldoctest
julia> t = Tensor('x', Tensor('y', Tensor('z', 'w')))
'x'⊗('y'⊗('z'⊗'w'))

julia> flatten(t)
'x'⊗'y'⊗'z'⊗'w'
```
