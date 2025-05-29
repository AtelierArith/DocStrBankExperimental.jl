```
hessian(f::Function, v::Union{SecondOrderTensor, Vec, Number})
hessian(f::Function, v::Union{SecondOrderTensor, Vec, Number}, :all)
```

Computes the hessian of the input function. If the (pseudo)-keyword `all` is given, the lower order results (gradient and value) of the function is also returned as a second and third output argument.

# Examples

```jldoctest
julia> A = rand(SymmetricTensor{2, 2});

julia> ∇∇f = hessian(norm, A)
2×2×2×2 SymmetricTensor{4, 2, Float64, 9}:
[:, :, 1, 1] =
  0.988034  -0.271765
 -0.271765  -0.108194

[:, :, 2, 1] =
 -0.271765   0.11695
  0.11695   -0.182235

[:, :, 1, 2] =
 -0.271765   0.11695
  0.11695   -0.182235

[:, :, 2, 2] =
 -0.108194  -0.182235
 -0.182235   1.07683

julia> ∇∇f, ∇f, f = hessian(norm, A, :all);
```
