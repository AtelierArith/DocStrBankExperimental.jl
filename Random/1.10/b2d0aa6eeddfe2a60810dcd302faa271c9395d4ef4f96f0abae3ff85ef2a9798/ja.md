```
randsubseq!([rng=default_rng(),] S, A, p)
```

[`randsubseq`](@ref)と同様ですが、結果は`S`に格納されます（必要に応じてサイズが変更されます）。

# 例

```jldoctest
julia> rng = MersenneTwister(1234);

julia> S = Int64[];

julia> randsubseq!(rng, S, 1:8, 0.3)
2-element Vector{Int64}:
 7
 8

julia> S
2-element Vector{Int64}:
 7
 8
```
