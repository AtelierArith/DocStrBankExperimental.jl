```
is_(x :: Array{T,1}; <keyword arguments>) where T<:Real
```

I-splineの基底を計算し、`ders`の導関数を`x`で評価するためのシグネチャ`(x:: Array{T,1}; ders :: Int = 0)`を持つ関数を返します。

キーワード引数には次のいずれかが含まれます：

1. `df`、場合によっては`intercept`と組み合わせて
2. `boundary_knots`と`interior_knots`
3. `knots`

# 引数

  * `boundary_knots :: Union{Tuple{T,T},Nothing} = nothing`: 境界ノット
  * `interior_knots :: Union{Array{T,1},Nothing} = nothing`: 内部ノット
  * `order :: Int = 4`: スプラインの次数
  * `intercept :: Bool = false`: インターセプト（1の列）を含めるかどうかのブール値。この動作は、Rのsplines2パッケージとは異なり、`intercept=FALSE`は最初のスプライン項を削除します。
  * `df :: Int = order + Int(intercept)`: 自由度
  * `knots :: Union{Array{T,1}, Nothing} = nothing`: 完全なノットのセット（重複を除く）

# 例

```jldoctest
julia> Splines2.is_(collect(0.0:0.2:1.0), df=3)(collect(0.0:0.2:1.0))
6×3 Array{Float64,2}:
 0.0     0.0     0.0   
 0.1808  0.0272  0.0016
 0.5248  0.1792  0.0256
 0.8208  0.4752  0.1296
 0.9728  0.8192  0.4096
 1.0     1.0     1.0   
```
