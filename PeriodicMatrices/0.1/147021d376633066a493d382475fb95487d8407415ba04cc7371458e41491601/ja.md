```
 ev = peigvals(A::Vector{Matrix}[, k = 1]; rev = true, fast = false)
```

`rev = true`（デフォルト）または`rev = false`の場合、`A(k-1)...*A(2)*A(1)*A(p)...*A(k)`の平方サイクリック積の固有値を計算します。引数`k`は開始インデックスを指定します（デフォルト: `k = 1`）。行列`A(1)`、`...`、`A(p)`は、`p`個の行列`A`のベクトルに含まれており、`i`番目の行列`A(i)`は、次元`m(i)×n(i)`で`A[i]`に含まれています。`fast = false`（デフォルト）の場合、固有値は周期的シュール分解に基づくアプローチを使用して計算されます[1]。一方、`fast = true`の場合、適切なリフトされたペンシルの構造を利用した削減[2]が使用されます。この後者のオプションは、行列の数が多い場合に不正確な結果をもたらすことがあります。

*注意:* `ev`の最初の`nmin`成分は、適切な行列積の`コア固有値`を含み、ここで`nmin`は行列`A[i]`の最小行次元であり、`i = 1, ..., p`の範囲です。一方、`ev`の最後の`ncur-nmin`成分はゼロであり、ここで`ncur`は`rev = true`の場合の`A[k]`の列次元、または`rev = false`の場合の`A[k]`の行次元です。

*参考文献*

[1] A. Bojanczyk, G. Golub, and P. Van Dooren,      The periodic Schur decomposition. Algorithms and applications, Proc. SPIE 1996.

[2] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
