compute*ρ*hat(fval*current, fval*next, gval*current, gval*next, hessian*current, d*k, θ, print_level)

ρ*hatを我々のアプローチに基づいて計算します：目的関数の実際の減少と、二次テイラー級数展開に基づく予測された減少の比率です。 ρ*hat = (fval*next - fval*current) / (-M*k + 0.5 * θ * min(||gval*current||, ||gval*next||) * ||d*k||)  ここで、M_k = 1/2 d ^ T * H * d + g ^ T  * d

# 入力:

```
- `fval_current::Float64`。現在の反復 x_k における関数値。
- `fval_next::Float64`。次の候補反復 x_k + d_k における関数値。
- `gval_current::Vector{Float64}`。現在の反復 x_k における勾配。
- `gval_next::Vector{Float64}`。次の候補反復 x_k + d_k における勾配。
- `hessian_current::Union{Matrix{Float64}, SparseMatrixCSC{Float64, Int64}, Symmetric{Float64, SparseMatrixCSC{Float64, Int64}}}`。
	現在の反復 x_k におけるヘッセ行列。
- `d_k::Vector{Float64}`。探索方向。
- `θ::Float64`。予測された減少に使用されるパラメータ。
- `print_level::Float64`。ログの冗長性レベル。
```

# 出力:

目的関数の実際の減少と、二次テイラー級数展開に基づく予測された減少の比率の値を表すスカラー。
