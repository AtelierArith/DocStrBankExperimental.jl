```
reverse_cols!(a::MatrixElem{T}) where T <: NCRingElement
```

$$
a
$$

の$i$番目と$r - i$番目の列を入れ替えます。ここで、$1 \leq i \leq c/2$であり、$c$は$a$の列数です。
