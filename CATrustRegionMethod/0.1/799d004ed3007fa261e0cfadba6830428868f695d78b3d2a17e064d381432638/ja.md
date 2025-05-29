computeSecondOrderModel(g, hessian_current,d)   現在の反復点周りの二次テイラー級数展開を計算します:   	1/2 d ^ T * H * d + g ^ T  * d (1)

# 入力:

```
- `g::Vector{Float64}`. 現在の反復点 x における勾配。
- `H::Union{Matrix{Float64}, SparseMatrixCSC{Float64, Int64}, Symmetric{Float64, SparseMatrixCSC{Float64, Int64}}}`.
	現在の反復点 x におけるヘッセ行列。
- `d::Vector{Float64}`. 探索方向。
```

# 出力:

現在の反復点周りの二次テイラー級数展開の値を表すスカラー。
