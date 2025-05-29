```
bs_(x :: Array{T,1}; <keyword arguments>) where T<:Real
```

Bスプラインの基底を計算し、`ders`の導関数を`x`で評価するための関数を返します。

キーワード引数には次のいずれかが含まれます：

1. `df`、場合によっては`intercept`と組み合わせて
2. `boundary_knots`と`interior_knots`
3. `knots`

# 引数

  * `boundary_knots :: Union{Tuple{T,T},Nothing} = nothing`: 境界ノット
  * `interior_knots :: Union{Array{T,1},Nothing} = nothing`: 内部ノット
  * `order :: Int = 4`: スプラインの次数
  * `intercept :: Bool = false`: 切片を含めるかどうかのブール値
  * `df :: Int = order - 1 + Int(intercept)`: 自由度
  * `knots :: Union{Array{T,1}, Nothing} = nothing`: ノットの完全なセット（重複を除く）
  * `centre :: Union{T,Nothing} = nothing)`: スプラインを中心にする値

# 例

```jldoctest
julia> Splines2.bs_(collect(0.0:0.2:1.0), df=3)(collect(0.0:0.2:1.0))
6×3 Array{Float64,2}:
 0.0    0.0    0.0  
 0.384  0.096  0.008
 0.432  0.288  0.064
 0.288  0.432  0.216
 0.096  0.384  0.512
 0.0    0.0    1.0  
```
