```
 ev = peigvals(A::Array{T,3}; rev = true, fast = false)
```

`rev = true`（デフォルト）である場合、`p` 個の正方行列 `A(p)...*A(2)*A(1)` の固有値を計算します（これを特性乗数とも呼びます）。`rev = false` の場合は `A(1)*A(2)...A(p)` の固有値を計算しますが、積を評価することはありません。行列 `A(1)`、`...`、`A(p)` は `n×n×p` 配列 `A` に含まれており、`i` 番目の行列 `A(i)` は `A[:,:,i]` に含まれています。`fast = false`（デフォルト）の場合、固有値は周期的シュール分解に基づくアプローチを使用して計算されます[1]。一方、`fast = true` の場合は、適切に持ち上げられたペンシルの構造を利用した削減[2]が使用されます。この後者のオプションは、行列の数が多い場合に不正確な結果をもたらすことがあります。

*参考文献*

[1] A. Bojanczyk, G. Golub, and P. Van Dooren,      The periodic Schur decomposition. Algorithms and applications, Proc. SPIE 1996.

[2] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
