```
gradient(f::Function, v::Union{SecondOrderTensor, Vec, Number})
gradient(f::Function, v::Union{SecondOrderTensor, Vec, Number}, :all)
```

Computes the gradient of the input function. If the (pseudo)-keyword `all` is given, the value of the function is also returned as a second output argument.

# Examples

```jldoctest
julia> A = rand(SymmetricTensor{2, 2});

julia> ∇f = gradient(norm, A)
2×2 SymmetricTensor{2, 2, Float64, 3}:
 0.374672  0.63107
 0.63107   0.25124

julia> ∇f, f = gradient(norm, A, :all);
```
