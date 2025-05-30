```
eye(),
eye(size::Integer)
```

単位行列を `DenseOperator` として返します。これは次のように定義されます：

$$
I = \begin{bmatrix}
    1 & 0 \\
    0 & 1
    \end{bmatrix}.
$$

`eye(size)` を呼び出すと、次元が `(size,size)` の単位行列 `DenseOperator` が生成されます。

# 例

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
