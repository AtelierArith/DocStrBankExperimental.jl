```
mgs(X::𝕄{T}, numCol::Int=0) where T<:RealOrComplex
```

修正された（安定化された）[グラム・シュミット直交化](https://bit.ly/2YE6zvy) は、実数または複素数要素から構成される正方行列または縦長行列 $X$ の列に対して行われます。直交化された $X$ は関数によって返されます。$X$ は変更されません。

デフォルトでは、すべての列が直交化されます。代わりに引数 `numCol` が提供されると、$X$ の最初の `numCol` 列のみが直交化されます。この場合、最初の `numCol` 列のみが返されます。

**例**

```julia
using LinearAlgebra, PosDefManifold
X=randn(10, 10);
U=mgs(X)        # 結果は 10⋅10
U=mgs(X, 3)     # 結果は 10⋅3
U'*U ≈ I ? println(" ⭐ ") : println(" ⛔ ")
# julia は次のことも理解します:
U'U ≈ I ? println(" ⭐ ") : println(" ⛔ ")
```
