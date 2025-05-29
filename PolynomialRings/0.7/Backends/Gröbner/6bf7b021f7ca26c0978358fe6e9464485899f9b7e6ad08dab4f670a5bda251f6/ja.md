```
basis, transformation = gröbner_transformation(polynomials)
```

`polynomials`によって生成されるイデアルのためのグレブナー基底と、`basis`の各要素がそのイデアルに含まれることを証明する`transformation`を返します（すなわち、`basis == transformation * polynomials`）。

これは、いくつかの標準的な最適化を用いてGWVアルゴリズムを使用して計算されます。詳細については[`PolynomialRings.GröbnerGWV.gwv`](@ref)を参照してください。
