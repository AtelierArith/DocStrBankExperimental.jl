```
reverse_rows(a::MatrixElem{T}) where T <: NCRingElement
```

行列 $a$ のエントリを持つ行列 $b$ を返します。ここで、$1 \leq i \leq r/2$ の場合に $i$ 行目と $r - i$ 行目が入れ替えられます。ここで $r$ は $a$ の行数です。
