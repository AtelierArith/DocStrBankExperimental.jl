```
LINV = invlyapop(A, E; disc = false, her = false)
```

`LINV`を定義します。これは、`disc = false`の場合の連続Lyapunov演算子`L:X -> AXE'+EXA'`の逆または、`disc = true`の場合の離散Lyapunov演算子`L:X -> AXA'-EXE'`の逆です。ここで、`(A,E)`は`n x n`行列のペアです。`her = false`の場合、逆Lyapunov演算子`LINV:Y -> X`は一般的な正方行列`Y`を一般的な正方行列`X`にマッピングし、関連する行列`M = Matrix(LINV)`は$n^2 \times n^2$です。`her = true`の場合、逆Lyapunov演算子`LINV:Y -> X`は対称/Hermitian行列`Y`を対称/Hermitian行列`X`にマッピングし、関連する行列`M = Matrix(LINV)`は$n(n+1)/2 \times n(n+1)/2$です。Lyapunov演算子の定義については、以下を参照してください。

M. Konstantinov, V. Mehrmann, P. Petkov. On properties of Sylvester and Lyapunov operators. Linear Algebra and its Applications 312:35–71, 2000.
