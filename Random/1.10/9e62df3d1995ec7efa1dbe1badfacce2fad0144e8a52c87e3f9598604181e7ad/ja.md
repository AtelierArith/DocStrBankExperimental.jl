```
rand!([rng=default_rng()], A, [S=eltype(A)])
```

配列 `A` にランダムな値を埋め込みます。`S` が指定されている場合（`S` は型またはコレクションであり、詳細については [`rand`](@ref) を参照）、値は `S` からランダムに選ばれます。これは `copyto!(A, rand(rng, S, size(A)))` と同等ですが、新しい配列を割り当てることはありません。

# 例

```jldoctest
julia> rng = MersenneTwister(1234);

julia> rand!(rng, zeros(5))
5-element Vector{Float64}:
 0.5908446386657102
 0.7667970365022592
 0.5662374165061859
 0.4600853424625171
 0.7940257103317943
```
