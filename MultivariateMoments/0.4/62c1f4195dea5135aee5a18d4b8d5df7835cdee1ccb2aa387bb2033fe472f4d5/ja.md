```
function BasisDependence{StaircaseDependence}(
    is_dependent::Function,
    basis::MB.AbstractPolynomialBasis,
)
```

*greedy sieve*アルゴリズムを使用して標準モノミアルの集合を計算します。このアルゴリズムは[LLR08, Algorithm 1]で提示されています。`basis`の外にあるモノミアルは独立していると仮定されます。それ以外の場合、`basis`内のインデックスが`i`であれば、`is_dependent`はそれが依存しているかどうかを返します。

[LLR08] Lasserre, Jean Bernard and Laurent, Monique, and Rostalski, Philipp. *ゼロ次元実根基理想の半正定値特性付けと計算.* Foundations of Computational Mathematics 8 (2008): 607-647.
