```
reverse_rows(a::MatrixElem{T}) where T <: NCRingElement
```

行列 $b$ を返します。ここで、$a$ のエントリを持ち、$1 \leq i \leq r/2$ の場合に $i$ 行目と $r - i$ 行目が入れ替わります。ここで $r$ は $a$ の行数です。
