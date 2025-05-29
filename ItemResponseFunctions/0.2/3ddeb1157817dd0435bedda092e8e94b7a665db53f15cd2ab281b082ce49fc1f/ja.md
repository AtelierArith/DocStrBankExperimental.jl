```julia
partial_credit(n; max_score)

```

スコア（0、`max_score`）にマッピングされる `n` の応答カテゴリを返すスコアリング関数。

## 例

```jldoctest
julia> my_partial_credit = partial_credit(4);

julia> my_partial_credit.(1:4)
4-element Vector{Float64}:
 0.0
 0.3333333333333333
 0.6666666666666666
 1.0
```

```jldoctest
julia> my_partial_credit = partial_credit(5, max_score = 3);

julia> my_partial_credit.(1:5)
5-element Vector{Float64}:
 0.0
 0.75
 1.5
 2.25
 3.0
```
