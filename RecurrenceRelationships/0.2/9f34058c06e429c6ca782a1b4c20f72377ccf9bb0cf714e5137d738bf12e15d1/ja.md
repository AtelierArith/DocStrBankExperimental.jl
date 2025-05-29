clenshaw!(f, c, A, B, C, x, ϕ₀)

は、DLMFで定義された再帰係数を含む `AbstractVector` である `A`、`B`、`C` において、係数 `c` の直交多項式展開を点 `x` で評価し、結果で `f` を上書きします。
