```
magnitude(lf::AbstractArray{T,3}, orientation::AbstractArray{T,2}) where {T<:Real}
```

リードフィールド `lf` の与えられた `orientation` に沿った大きさを返します。

# 引数

  * `lf::AbstractArray{T,3}`: 次元が `electrodes x sources x spatial dimension` のリードフィールド。
  * `orientation::AbstractArray{T,2}`: 次元が `sources x spatial dimensions` のソースの向き。

# 例

```julia-repl
# リードフィールドを指定する（通常はヘッドモデルによって与えられる）
julia> lf = cat([1 0; 0 1; 0 0], [1 1; 0 0; 0.5 0.5], dims=3);

# ソースの向きを指定する
julia> ori = [1.0 0; 0 1]

# 大きさを計算する
julia> magnitude(lf, ori)
3×2 Matrix{Float64}:
 1.0  1.0
 0.0  0.0
 0.0  0.5
```
