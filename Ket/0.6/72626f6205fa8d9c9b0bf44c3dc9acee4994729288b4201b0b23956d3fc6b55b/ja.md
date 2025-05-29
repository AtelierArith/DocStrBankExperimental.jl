```
random_unitary([T=ComplexF64,] d::Integer)
```

次元 `d` のHaarランダムユニタリ行列を生成します。`T` が実数型の場合、出力は代わりにHaarランダム（実数の）直交行列になります。

参考文献: Gilbert W. Stewart, [doi:10.1137/0717034](https://doi.org/10.1137/0717034)             Demmel et al., [lawn203](http://www.netlib.org/lapack/lawnspdf/lawn203.pdf)
