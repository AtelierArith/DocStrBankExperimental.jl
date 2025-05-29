```
function det1(X::AnyMatrix; <tol::Real=0.>)
```

引数行列 $X$ を *単位行列式* を持つように正規化して返します。正方行列の正定値行列に対しては、これは [特別線形群](https://bit.ly/2W5jDZ6) の行列の集合からの最良の近似です - Bhatia と Jain (2014) を参照してください[🎓](@ref)。

$$
X
$$

は実数または複素数の `Diagonal`、`LowerTriangular`、`Matrix`、または `Hermitian` 行列である可能性があります。（[AnyMatrix 型](@ref) を参照）

行列式が `tol` より大きくない場合（デフォルトはゼロ）、警告が表示され、$X$ が返されます。

!!! note "Nota Bene"
    この関数は正定値行列を対象としています。行列が欠陥がある場合、Julia は行列式を計算中にエラーをスローする可能性があります。


**参照**: [Julia det 関数](https://bit.ly/2Y4MnTF)。

**関連**: [`tr1`](@ref)。

**例**

```julia
using LinearAlgebra, PosDefManifold
P=randP(5) # 5x5 のランダムな実正定値行列を生成
Q=det1(P)
det(Q) # 1 である必要があります
# トレランスを使用
Q=det1(P; tol=1e-12)
```
