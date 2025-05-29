```
SetGranularity(p::DSProblem{T}, granularities)
```

複数の変数の粒度を設定します。粒度は、`granularities` に `key => value` ペアのコレクションとして提供される必要があります。ここで、key は変数のインデックスで、value は粒度です。

# 例

```jldoctest
julia> p = DSProblem(3; objective=x->sum(x.^2), initial_point=[0.25, 0.1, 1.0]);

julia> granularities = Dict( 1 => 0.1, 2 => 0.2, 3 => 0.3 )
Dict{Int64, Float64} with 3 entries:
  2 => 0.2
  3 => 0.3
  1 => 0.1

julia> SetGranularity(p, granularities)
```

ベクトルを使用して粒度を設定することもでき、`granularities[index]` は `index` の変数の粒度を `granularities[index]` で設定します。

```jldoctest
julia> p = DSProblem(3; objective=x->sum(x.^2), initial_point=[0.25, 0.1, 1.0]);

julia> granularities = [0.1; 0.2; 0.3]
3-element Vector{Float64}:
 0.1
 0.2
 0.3

julia> SetGranularity(p, granularities)
```
