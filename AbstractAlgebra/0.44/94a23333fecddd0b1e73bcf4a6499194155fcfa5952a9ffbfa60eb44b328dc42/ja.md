```
swap_cols!(a::MatrixElem{T}, i::Int, j::Int) where T <: NCRingElement
```

$$
a
$$

の$i$番目と$j$番目の列をその場で入れ替えます。この関数は変更された行列を返します（行列はAbstractAlgebra.jlで可変であると仮定されています）。
