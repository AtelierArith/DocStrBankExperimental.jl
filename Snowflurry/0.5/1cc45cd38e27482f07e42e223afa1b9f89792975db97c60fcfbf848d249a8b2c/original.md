```
eye(),
eye(size::Integer)
```

Return the identity matrix as a `DenseOperator`, which is defined as:

$$
I = \begin{bmatrix}
    1 & 0 \\
    0 & 1
    \end{bmatrix}.
$$

Calling `eye(size)` will produce an identity matrix `DenseOperator`  with dimensions `(size,size)`.

# Examples

```jldoctest
julia> eye()
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im

julia> eye(4)
(4, 4)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im

```
