```
struct BasisDependence{D,B<:MB.AbstractPolynomialBasis}
    basis::B
    dependence::Vector{D}
end
```

基底の要素間の依存関係。

!!! tip
    変数の数が2または3の場合、Plots.jlを使用して視覚化できます。

