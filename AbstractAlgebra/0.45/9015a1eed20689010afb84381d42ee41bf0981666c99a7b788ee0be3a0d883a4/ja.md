```
multiply_column(a::MatrixElem{T}, s::RingElement, i::Int, rows = 1:nrows(a)) where T <: RingElement
```

$$
a
$$

のコピーを作成し、$a$の$i$番目の列を$s$で乗算します。

デフォルトでは、変換は$a$のすべての行に適用されます。これはオプションの`rows`引数を使用して変更できます。
