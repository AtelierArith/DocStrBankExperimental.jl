```
LinearOperator(type::Type{T}, nrow, ncol, symmetric, hermitian, prod!,
                [tprod!=nothing, ctprod!=nothing],
                S = Vector{T}) where {T}
```

Construct a linear operator from functions where the type is specified as the first argument. Change `S` to use LinearOperators on GPU. Notice that the linear operator does not enforce the type, so using a wrong type can result in errors. For instance,

```
A = [im 1.0; 0.0 1.0] # Complex matrix
function mulOp!(res, M, v, α, β)
  mul!(res, M, v, α, β)
end
op = LinearOperator(Float64, 2, 2, false, false, 
                    (res, v, α, β) -> mulOp!(res, A, v, α, β), 
                    (res, u, α, β) -> mulOp!(res, transpose(A), u, α, β), 
                    (res, w, α, β) -> mulOp!(res, A', w, α, β))
Matrix(op) # InexactError
```

The error is caused because `Matrix(op)` tries to create a Float64 matrix with the contents of the complex matrix `A`.

Using `*` may generate a vector that contains `NaN` values. This can also happen if you use the 3-args `mul!` function with a preallocated vector such as  `Vector{Float64}(undef, n)`. To fix this issue you will have to deal with the cases `β == 0` and `β != 0` separately:

```
d1 = [2.0; 3.0]
function mulSquareOpDiagonal!(res, d, v, α, β::T) where T
  if β == zero(T)
    res .= α .* d .* v
  else 
    res .= α .* d .* v .+ β .* res
  end
end
op = LinearOperator(Float64, 2, 2, true, true, 
                    (res, v, α, β) -> mulSquareOpDiagonal!(res, d, v, α, β))
```

It is possible to create an operator with the 3-args `mul!`. In this case, using the 5-args `mul!` will generate storage vectors.

```
A = rand(2, 2)
op = LinearOperator(Float64, 2, 2, false, false, 
                    (res, v) -> mul!(res, A, v),
                    (res, w) -> mul!(res, A', w))
```

The 3-args `mul!` also works when applying the operator on a matrix.
