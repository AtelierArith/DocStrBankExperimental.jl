```
ns_(x :: Array{T,1}; <keyword arguments>) where T<:Real
```

自然Bスプラインの基底を計算し、`ders`の導関数を`x`で評価するための関数を返します。

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
julia> Splines2.ns_(collect(0.0:0.2:1.0), df=3)(collect(0.0:0.2:1.0))
6×3 Array{Float64,2}:
  0.0       0.0        0.0     
 -0.100444  0.409332  -0.272888
  0.102383  0.540852  -0.359235
  0.501759  0.386722  -0.172481
  0.418872  0.327383   0.217745
 -0.142857  0.428571   0.714286
```
