```
roots(f::Generic.Poly{AbsSimpleNumFieldElem}; max_roots = degree(f),
                                ispure = false,
                                is_squarefree = false,
                                is_normal = false)       -> Vector{AbsSimpleNumFieldElem}
```

多項式 $f$ の根を計算します。

  * `max_roots` は、関数が返す根の最大数を制御します。
  * `ispure` は、$f$ が $x^d + c$ の形であるかどうかを示します。ここで、$d$ は次数、$c$ は $f$ の定数項です。
  * `is_normal` は、体が $f$ の根を含まないか、すべての根を含むことを示します。
  * `is_squarefree` は、多項式がすでに平方フリーであることが知られているかどうかを示します。
