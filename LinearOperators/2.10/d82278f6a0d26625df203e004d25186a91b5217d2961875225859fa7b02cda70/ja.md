solve*shifted*system!(x, B,  b, σ)

線形システム (B + σI) x = b を解きます。ここで、B は前方 L-BFGS 演算子であり、σ ≥ 0 です。

### パラメータ

  * `x::AbstractVector{T}`: 解 x を格納するために使用される長さ n の事前割り当てベクトル。
  * `B::LBFGSOperator`: サイズ n x n の行列をモデル化する前方 L-BFGS 演算子。
  * `b::AbstractVector{T}`: 長さ n の右辺ベクトル。
  * `σ::T`: 非負のシフト。

### 戻り値

  * `x::AbstractVector{T}`: 長さ n の解ベクトル `x`。

### メソッド

このメソッドは、シフト `σ` を処理するための修正を加えた二重ループ再帰のようなアプローチを使用します。

### 例

```julia
using Random

# 問題の設定
n = 100  # 問題のサイズ
mem = 10   # L-BFGS メモリサイズ
scaling = true  # スケーリングを有効にする

# L-BFGS 演算子を作成
B = LBFGSOperator(n, mem = mem, scaling = scaling)

# L-BFGS 演算子にランダムな {s, y} ペアを追加
for _ = 1:10
    s = rand(n)   
    y = rand(n)   
    push!(B, s, y)  # {s, y} ペアを B に追加
end

# システムのためのベクトルを準備
x = zeros(n)   # 事前割り当てされた解ベクトル
b = rand(n)        # 右辺ベクトル
σ = 0.1            # 小さなシフト値

# シフトされたシステムを解く
result = solve_shifted_system!(x, B, b, σ)

# 解が十分に近いことを確認する（残差テスト）
@assert norm(B * x + σ * x - b) / norm(b) < 1e-8
```

### 参考文献

Erway, J. B., Jain, V., & Marcia, R. F. Shifted L-BFGS Systems. Optimization Methods and Software, 29(5), pp. 992-1004, 2014.
