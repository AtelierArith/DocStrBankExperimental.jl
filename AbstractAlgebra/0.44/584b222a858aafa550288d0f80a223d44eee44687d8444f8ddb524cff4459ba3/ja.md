```
reverse_cols(a::MatrixElem{T}) where T <: NCRingElement
```

行列 $b$ を返します。ここで、$a$ のエントリを持ち、$1 \leq i \leq c/2$ の場合に $i$ 番目の列と $r - i$ 番目の列が入れ替わります。ここで $c$ は $a$ の列数です。
