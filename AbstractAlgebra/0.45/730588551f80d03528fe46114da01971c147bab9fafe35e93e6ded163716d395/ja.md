```
add_column(a::MatrixElem{T}, s::RingElement, i::Int, j::Int, rows = 1:nrows(a)) where T <: RingElement
```

$$
a
$$

のコピーを作成し、$s$を$i$-行目に掛けて$j$-行目に加えます。

デフォルトでは、変換は$a$のすべての行に適用されます。これはオプションの`rows`引数を使用して変更できます。
