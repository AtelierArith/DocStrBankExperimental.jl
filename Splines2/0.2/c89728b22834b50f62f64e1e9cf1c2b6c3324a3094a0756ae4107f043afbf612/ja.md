```
ms(x :: Array{T,1}; <keyword arguments>) where T<:Real
```

Mスプラインの基底を計算します。

キーワード引数には次のいずれかが含まれます：

1. `df`、場合によっては `intercept` と組み合わせて
2. `boundary_knots` と `interior_knots`
3. `knots`

# 引数

  * `boundary_knots :: Union{Tuple{T,T},Nothing} = nothing`: 境界ノット
  * `interior_knots :: Union{Array{T,1},Nothing} = nothing`: 内部ノット
  * `order :: Int = 4`: スプラインの次数
  * `intercept :: Bool = false`: 切片を含めるかどうかのブール値
  * `df :: Int = order - 1 + Int(intercept)`: 自由度
  * `knots :: Union{Array{T,1}, Nothing} = nothing`: ノットの完全なセット（重複を除く）
  * `centre :: Union{T,Nothing} = nothing)`: スプラインを中心にする値
  * `ders :: Int = 0`: スプラインの導関数

# 例

```jldoctest
julia> Splines2.ms(collect(0.0:0.2:1.0), df=3)
6×3 Array{Float64,2}:
 0.0    0.0    0.0  
 1.536  0.384  0.032
 1.728  1.152  0.256
 1.152  1.728  0.864
 0.384  1.536  2.048
 0.0    0.0    4.0  
```
