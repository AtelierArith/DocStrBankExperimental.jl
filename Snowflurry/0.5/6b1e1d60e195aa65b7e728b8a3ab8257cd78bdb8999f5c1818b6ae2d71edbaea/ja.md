```
get_embed_operator(op::DenseOperator, target_body_index::Int, system::MultiBodySystem)
```

特定のボディ（例：キュービット）に対して定義されたローカルオペレーター（`op`）を使用して、`system`によって与えられた多体システムのヒルベルト空間に対応するオペレーターを構築します。

# 例

```jldoctest
julia> system = MultiBodySystem(3, 2)
Snowflurry.Multibody system with 3 bodies
   Hilbert space structure:
   [2, 2, 2]

julia> x = sigma_x()
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    1.0 + 0.0im    .

julia> X_1 = get_embed_operator(x, 1, system)
(8, 8)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im


```
