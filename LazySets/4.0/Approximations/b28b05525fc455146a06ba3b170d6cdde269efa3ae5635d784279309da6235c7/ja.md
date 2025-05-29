```
overapproximate(P::SimpleSparsePolynomialZonotope, ::Type{<:Zonotope},
                dom::IntervalBox)
```

単純スパース多項式ゾノトープ `dom` のパラメータ領域に対してゾノトープで上近似します。

### 入力

  * `P`         – 単純スパース多項式ゾノトープ
  * `Zonotope`  – 目標集合の型
  * `dom`       – パラメータ領域で、`[-1, 1]^q` の部分集合である必要があります、                ここで `q = nparams(P)`

### 出力

ゾノトープ。
