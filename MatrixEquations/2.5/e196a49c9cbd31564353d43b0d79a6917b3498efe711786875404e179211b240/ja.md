```
L = lyapop(A; disc = false, her = false)
```

`A`が`n x n`行列であるとき、連続リャプノフ演算子`L:X -> AX+XA'`は`disc = false`の場合に定義され、離散リャプノフ演算子`L:X -> AXA'-X`は`disc = true`の場合に定義されます。`her = false`の場合、リャプノフ演算子`L:X -> Y`は一般の正方行列`X`を一般の正方行列`Y`にマッピングし、関連する行列`M = Matrix(L)`は$n^2 \times n^2$です。`her = true`の場合、リャプノフ演算子`L:X -> Y`は対称/エルミート行列`X`を対称/エルミート行列`Y`にマッピングし、関連する行列`M = Matrix(L)`は$n(n+1)/2 \times n(n+1)/2$です。リャプノフ演算子の定義については、以下を参照してください：

M. Konstantinov, V. Mehrmann, P. Petkov. On properties of Sylvester and Lyapunov operators. Linear Algebra and its Applications 312:35–71, 2000.
