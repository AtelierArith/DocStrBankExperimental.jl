```
aaa(y, z)
aaa(f)
```

適応的に有理補間を計算します。

# 引数

## 離散モード

  * `y::AbstractVector{<:Number}`: ノードでの値
  * `z::AbstractVector{<:Number}`: 補間ノード

## 連続モード

  * `f::Function`: 区間[-1,1]で近似する関数

# キーワード引数

  * `max_degree::Integer=150`: 使用する最大分子/分母の次数
  * `float_type::Type=Float64`: 計算に使用する浮動小数点型
  * `tol::Real=1000*eps(float_type)`: 停止のための許容誤差
  * `stagnation::Integer=10`: 停滞を決定するための反復回数
  * `stats::Bool=false`: 収束統計を返す

# 戻り値

  * `r::Barycentric`: 有理補間
  * `stats::NamedTuple`: キーワード`stats=true`の場合の収束統計

# 例

```julia-repl
julia> z = 1im * range(-10, 10, 500);

julia> y = @. exp(z);

julia> r = aaa(z, y);

julia> degree(r)   # 分子と分母の両方
12

julia> first(nodes(r), 4)
4-element Vector{ComplexF64}:
 0.0 - 6.272545090180361im
 0.0 + 9.43887775551102im
 0.0 - 1.1022044088176353im
 0.0 + 4.909819639278557im

julia> r(1im * π / 2)
-2.637151617496356e-15 + 1.0000000000000002im
```

関数を曲線または領域上で近似するための[`approximate`](@ref)も参照してください。
