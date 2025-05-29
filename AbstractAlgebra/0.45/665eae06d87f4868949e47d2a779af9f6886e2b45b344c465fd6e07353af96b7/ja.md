```
multiply_row!(a::MatrixElem{T}, s::RingElement, i::Int, cols = 1:ncols(a)) where T <: RingElement
```

$$
a
$$

の$i$行目を$s$で乗算します。

デフォルトでは、変換は$a$のすべての列に適用されます。これはオプションの`cols`引数を使用して変更できます。
