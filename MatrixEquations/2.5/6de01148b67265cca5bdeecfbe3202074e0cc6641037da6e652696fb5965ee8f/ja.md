```
L = lyapop(A, E; disc = false, her = false)
```

`(A,E)` のペアに対して、連続リャプノフ演算子 `L:X -> AXE'+EXA'` を定義します（`disc = false` の場合）または離散リャプノフ演算子 `L:X -> AXA'-EXE'` を定義します（`disc = true` の場合）。`her = false` の場合、リャプノフ演算子 `L:X -> Y` は一般の正方行列 `X` を一般の正方行列 `Y` にマッピングし、関連する行列 `M = Matrix(L)` は $n^2 \times n^2$ です。`her = true` の場合、リャプノフ演算子 `L:X -> Y` は対称/エルミート行列 `X` を対称/エルミート行列 `Y` にマッピングし、関連する `M = Matrix(L)` は $n(n+1)/2 \times n(n+1)/2$ です。リャプノフ演算子の定義については、以下を参照してください：

M. Konstantinov, V. Mehrmann, P. Petkov. On properties of Sylvester and Lyapunov operators. Linear Algebra and its Applications 312:35–71, 2000.
