```
@varform <form-definition>
```

Juliaのフォームコンパイラは、JuliaパーサーとASTのメタプログラミングに基づくトラバーサルを使用して、広く普及している数学的慣習に密接に従ったExprから変分定式の記述に必要なすべての情報を含む構造を作成します。

例:

```
EFIE = @varform T[k,j] = e[k]
MFIE = @varform 0.5*I[k,j] + K[k,j] = h[k]
PMCH = @varform M[k,j] - η*T[k,m] + 1/η*T[l,j] + M[l,m] = e[k] + h[l]
```
