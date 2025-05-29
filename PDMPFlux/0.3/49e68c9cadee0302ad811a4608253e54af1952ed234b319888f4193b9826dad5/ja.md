```
ZigZag(dim::Int, ∇U::Function; grid_size::Int=10, tmax::Float64=1.0, 
    vectorized_bound::Bool=true, signed_bound::Bool=true, adaptive::Bool=true, kwargs...)
```

# コンストラクタの引数

  * `dim::Int`: 空間の次元。
  * `∇U::Function`: ポテンシャルエネルギー関数の勾配。
  * `grid_size::Int`: 空間を離散化するためのグリッドポイントの数。デフォルトは10。
  * `tmax::Float64`: グリッドのホライズン。デフォルトは1.0。0の場合、適応的なtmaxが使用されます。
  * `vectorized_bound::Bool`: 境界にベクトル化された戦略を使用するかどうか。デフォルトはtrue。
  * `signed_bound::Bool`: 符号付き境界戦略を使用するかどうか。デフォルトはtrue。
  * `adaptive::Bool`: 適応的なtmaxを使用するかどうか。デフォルトはtrue。
  * `kwargs...`: その他のキーワード引数。

# ZigZag構造体の属性

  * `dim::Int`: 空間の次元。
  * `refresh_rate::Float64`: リフレッシュレート。
  * `∇U::Function`: ポテンシャルの勾配。
  * `grid_size::Int`: 空間を離散化するためのグリッドポイントの数。
  * `tmax::Float64`: グリッドのtmax。
  * `adaptive::Bool`: 適応的なtmaxを使用するかどうか。
  * `vectorized_bound::Bool`: ベクトル化された戦略を使用するかどうか。
  * `signed_bound::Bool`: 符号付き戦略を使用するかどうか。
  * `flow::Function`: インテグレータ関数。
  * `rate::Array`: プロセスのレート。
  * `rate_vect::Array`: ベクトル化されたレート。
  * `signed_rate::Array`: 符号付きレート。
  * `signed_rate_vect::Array`: ベクトル化され符号付きのレート。
  * `velocity_jump::Function`: 速度ジャンプ関数。
  * `state`: ZigZagサンプラーの状態。
