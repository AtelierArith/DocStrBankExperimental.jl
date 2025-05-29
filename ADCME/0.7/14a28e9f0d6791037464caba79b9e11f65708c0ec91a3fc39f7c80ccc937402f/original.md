```
solve_batch(A::Union{PyObject, Array{<:Real, 2}}, rhs::Union{PyObject, Array{<:Real,2}})
```

Solves $Ax = b$ for a batch of right hand sides. 

  * `A`: a $m\times n$ matrix, where $m\geq n$
  * `rhs`: a $n_b\times m$ matrix. Each row is a new right hand side to solve.

The returned value is a $n_b\times n$ matrix. 

# Example

```julia
a = rand(10,5)
b = rand(100, 10)
sol = solve_batch(a, b)
@assert run(sess, sol) ≈ (a\b')'
```

!!! note
    Internally, the matrix $A$ is factorized first and then the factorization is used to solve multiple right hand side.

