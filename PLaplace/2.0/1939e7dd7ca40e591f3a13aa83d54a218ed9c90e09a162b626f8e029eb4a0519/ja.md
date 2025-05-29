```julia
mutable struct ErrorData
```

解析解と比較したエラー値を保持する構造体。複数の計算に使用でき、プロットを生成するために使用できます。

# フィールド

  * `p::Vector{Float64}`: PDEパラメータ。
  * `n::Vector{Int64}`: グリッドポイントの数
  * `eps::Vector{Float64}`: 精度
  * `errors::Vector{Vector{Float64}}`: エラー
