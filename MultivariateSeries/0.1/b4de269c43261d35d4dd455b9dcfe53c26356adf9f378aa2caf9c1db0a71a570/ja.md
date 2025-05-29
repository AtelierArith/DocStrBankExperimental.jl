```
series(f::Function, L::Vector{M}) -> Series{C,M}
```

関数 $f: \mathbb{N}^n \rightarrow C$ と単項式の列 L に対して、生成系列 $\sum_{x^{α} \in L} f(α) z^α$ を計算します。
