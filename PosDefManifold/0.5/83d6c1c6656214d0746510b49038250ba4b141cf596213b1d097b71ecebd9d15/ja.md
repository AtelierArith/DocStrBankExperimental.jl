```
gram(X::Matrix{T}) where T<:RealOrComplex
```

与えられた一般的なデータ行列 $X$ は、実数または複素数の要素で構成されており、正規化された [Gram 行列](https://bit.ly/2I0FQn2) を返します。これは、サンプルサイズで修正された $X$ の共分散行列ですが、平均を引くことはありません。

結果は `Hermitian` としてフラグ付けされます。 [行列の型変換](@ref) を参照してください。

!!! note "Nota Bene"
    $$
    X
    $$

    が広いまたは正方形の場合 (r<=c)、$XX^H/c$ を返します。$X$ が高い場合 (r>c)、$X^HX/r$ を返します。


**例**

```julia
using PosDefManifold
X=randn(5, 150);
G=gram(X) # => G=X*X'/150
X=randn(100, 2);
F=gram(X); # => G=X'*X/100
```
