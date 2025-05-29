```
reverse_rows!(a::MatrixElem{T}) where T <: NCRingElement
```

$$
a
$$

の$i$行目と$r - i$行目を入れ替えます。ここで、$1 \leq i \leq r/2$であり、$r$は$a$の行数です。
