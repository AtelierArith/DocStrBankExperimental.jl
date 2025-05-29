```
reverse_cols!(a::MatrixElem{T}) where T <: NCRingElement
```

$$
a
$$

の$i$列目と$r - i$列目を入れ替えます。ここで、$1 \leq i \leq c/2$であり、$c$は$a$の列数です。
