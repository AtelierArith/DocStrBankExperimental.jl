```
group_indices(x) -> Dict
```

ベクトル `x` に含まれる各異なる値の要素のインデックスを計算します。この情報は、層別サンプリングなどの再サンプリング戦略に役立ちます。

関連情報として [`group_counts`](@ref) も参照してください。

# 例

```jldoctest
julia> x = [:yes, :no, :maybe, :yes];

julia> group_indices(x)
Dict{Symbol, Vector{Int64}} with 3 entries:
  :yes   => [1, 4]
  :maybe => [3]
  :no    => [2]
```
