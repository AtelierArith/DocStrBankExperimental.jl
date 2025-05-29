```
UL <: Factorization
```

正方行列 `A` の `UL` 因数分解の行列因数分解型です。これは、対応する行列因数分解関数 [`ul`](@ref) の戻り値の型です。

因数分解 `F::UL` の個々のコンポーネントには [`getproperty`](@ref) を介してアクセスできます：

| コンポーネント | 説明                    |
|:------- |:--------------------- |
| `F.U`   | `UL` の `U` (上三角) 部分   |
| `F.L`   | `UL` の `L` (単位下三角) 部分 |
| `F.p`   | (右) 順列 `Vector`       |
| `F.P`   | (右) 順列 `Matrix`       |

因数分解を反復すると、コンポーネント `F.U`、`F.L`、および `F.p` が得られます。

# 例

```jldoctest
julia> A = [4 3; 6 3]
2×2 Array{Int64,2}:
 4  3
 6  3

julia> F = ul(A)
UL{Float64,Array{Float64,2}}
L 因子:
2×2 Array{Float64,2}:
 1.0       0.0
 0.666667  1.0
U 因子:
2×2 Array{Float64,2}:
 6.0  3.0
 0.0  1.0

julia> F.L * F.U == A[F.p, :]
true

julia> l, u, p = ul(A); # 反復による分解

julia> l == F.L && u == F.U && p == F.p
true
```
