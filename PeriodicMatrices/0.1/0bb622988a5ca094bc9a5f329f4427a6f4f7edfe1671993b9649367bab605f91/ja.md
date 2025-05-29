cm = pseig(A::PeriodicMatrix[, k = 1]; fast = false) 

離散時間周期行列 `A(t)` の特性乗数を計算します。 `A` は `PeriodicMatrix` として与えられます。特性乗数は、成分行列の逆積の固有値として計算され、積を評価することはありません。引数 `k` は成分行列の開始インデックスを指定します（デフォルト: `k = 1`）。 `fast = false`（デフォルト）の場合、固有値は周期シュール分解に基づくアプローチを使用して計算されます[1]。一方、`fast = true` の場合は、適切なリフトペンシルの構造を利用した削減[2]が使用されます。この後者のオプションは、行列の数が多い場合に不正確な結果をもたらすことがあります。

*注:* `cm` の最初の `nmin` 成分は `コア特性乗数` を含み、ここで `nmin` は成分行列の最小行次元です。一方、`cm` の最後の `ncur-nmin` 成分はゼロであり、ここで `ncur` は `k` 番目の成分行列の列次元です。

*参考文献*

[1] A. Bojanczyk, G. Golub, and P. Van Dooren,      The periodic Schur decomposition. Algorithms and applications, Proc. SPIE 1996.

[2] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
