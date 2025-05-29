```
swap_cols!(a::MatrixElem{T}, i::Int, j::Int) where T <: NCRingElement
```

$$
a
$$

の$i$番目と$j$番目の列をその場で入れ替えます。この関数は、行列がAbstractAlgebra.jlで可変であると仮定されているため、変更された行列を返します。
