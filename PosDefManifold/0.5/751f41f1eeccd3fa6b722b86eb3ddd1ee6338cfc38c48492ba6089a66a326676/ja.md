```
tr1(X::AnyMatrix; tol::Real=0.)
```

引数行列 $X$ を *単位トレース* を持つように正規化して返します。

$$
X
$$

は実数または複素数の `Diagonal`、`LowerTriangular`、`Matrix` または `Hermitian` 行列であることができます（[AnyMatrix type](@ref) を参照）。そのトレースは実数でなければなりません。もしその虚部の絶対値が `tol`（デフォルトはゼロ）を超える場合、警告が表示され、$X$ が返されます。また、トレースが `tol` より大きくない場合も警告が表示され、$X$ が返されます。

**参照**: [Julia trace function](https://bit.ly/2HoOLiM)。

**関連**: [`tr`](@ref)、[`det1`](@ref)。

**例**

```julia
using LinearAlgebra, PosDefManifold

P=randP(5) # 5x5 のランダムな実正定値行列を生成
Q=tr1(P)
tr(Q)  # 1 である必要があります
# 許容誤差を使用
Q=tr1(P; tol=1e-12)

Pc=randP(ComplexF64, 5) # 5x5 のランダムな実正定値行列を生成
Qc=tr1(Pc)
tr(Qc)  # 1 である必要があります
```
