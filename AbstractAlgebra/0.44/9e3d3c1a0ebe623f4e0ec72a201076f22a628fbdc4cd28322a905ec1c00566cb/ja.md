```
add_row!(a::MatrixElem{T}, s::RingElement, i::Int, j::Int, cols = 1:ncols(a)) where T <: RingElement
```

$$
a
$$

の$j$-行目に$i$-行目の$s$倍を加えます。

デフォルトでは、変換は$a$のすべての列に適用されます。これはオプションの`cols`引数を使用して変更できます。
