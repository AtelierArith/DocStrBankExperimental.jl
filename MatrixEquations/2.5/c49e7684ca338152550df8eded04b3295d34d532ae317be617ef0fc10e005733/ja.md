```
LINV = invlyapop(A; disc = false, her = false)
```

`LINV`を定義します。これは、`disc = false`の場合の連続リャプノフ演算子`L:X -> AX+XA'`の逆または、`disc = true`の場合の離散リャプノフ演算子`L:X -> AXA'-X`の逆です。ここで、`A`は`n x n`行列です。`her = false`の場合、逆リャプノフ演算子`LINV:Y -> X`は一般の正方行列`Y`を一般の正方行列`X`にマッピングし、関連する行列`M = Matrix(LINV)`は$n^2 \times n^2$です。`her = true`の場合、逆リャプノフ演算子`LINV:Y -> X`は対称/エルミート行列`Y`を対称/エルミート行列`X`にマッピングし、関連する行列`M = Matrix(LINV)`は$n(n+1)/2 \times n(n+1)/2$です。リャプノフ演算子の定義については、以下を参照してください。

M. Konstantinov, V. Mehrmann, P. Petkov. On properties of Sylvester and Lyapunov operators. Linear Algebra and its Applications 312:35–71, 2000.
