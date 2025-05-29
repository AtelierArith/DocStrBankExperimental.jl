```
solve_batch(A::Union{PyObject, Array{<:Real, 2}}, rhs::Union{PyObject, Array{<:Real,2}})
```

$$
Ax = b
$$

の右辺のバッチを解きます。

  * `A`: $m\times n$ 行列で、$m\geq n$ です。
  * `rhs`: $n_b\times m$ 行列です。各行は解くための新しい右辺です。

返される値は $n_b\times n$ 行列です。

# 例

```julia
a = rand(10,5)
b = rand(100, 10)
sol = solve_batch(a, b)
@assert run(sess, sol) ≈ (a\b')'
```

!!! note
    内部的に、行列 $A$ は最初に因子分解され、その後因子分解が複数の右辺を解くために使用されます。

