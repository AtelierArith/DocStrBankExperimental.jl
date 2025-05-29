```
 cm = pseig(A::PeriodicArray; fast = false)
```

離散時間周期行列 `A(t)` の特性乗数を計算します。 `A` は `PeriodicArray` として与えられます。特性乗数は、積を評価することなく、成分行列の逆積の固有値として計算されます。 `fast = false`（デフォルト）の場合、固有値は周期シュア分解に基づくアプローチを使用して計算されます[1]。一方、`fast = true` の場合は、適切なリフトペンシルの構造を利用した削減[2]が使用されます。この後者のオプションは、大量の行列に対して不正確な結果をもたらすことがあります。

*参考文献*

[1] A. Bojanczyk, G. Golub, and P. Van Dooren,      The periodic Schur decomposition. Algorithms and applications, Proc. SPIE 1996.

[2] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
