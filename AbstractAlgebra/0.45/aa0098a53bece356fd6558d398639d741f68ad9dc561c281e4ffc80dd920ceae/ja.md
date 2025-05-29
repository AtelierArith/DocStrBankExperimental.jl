```
add_column!(a::MatrixElem{T}, s::RingElement, i::Int, j::Int, rows = 1:nrows(a)) where T <: RingElement
```

$$
a
$$

の$j$-行目に$i$-行目の$s$倍を加えます。

デフォルトでは、変換は$a$のすべての行に適用されます。これはオプションの`rows`引数を使用して変更できます。
