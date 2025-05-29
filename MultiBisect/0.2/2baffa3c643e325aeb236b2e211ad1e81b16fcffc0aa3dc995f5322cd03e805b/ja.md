```
marchingsquares(edge)
```

エッジの中点を返します。これは、[マーチングスクエアアルゴリズム](https://en.wikipedia.org/wiki/Marching_squares)に似た方法で行われます。関数評価は必要ありません。

# 例

```jldoctest
julia> f(x) = 1 - sum(abs2, x); # 単位円

julia> BG = bisect(f, (0.0:1.0, 0.0:1.0); iterations=3);


julia> E = edges(BG)
8-element Vector{Tuple{Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 ((0.75, 0.0), (1.0, 0.0))
 ((0.75, 0.25), (1.0, 0.25))
 ((0.75, 0.5), (1.0, 0.5))
 ((0.75, 0.5), (0.75, 0.75))
 ((0.0, 0.75), (0.0, 1.0))
 ((0.25, 0.75), (0.25, 1.0))
 ((0.5, 0.75), (0.75, 0.75))
 ((0.5, 0.75), (0.5, 1.0))

julia> marchingsquares.(E)
8-element Vector{Tuple{Float64, Float64}}:
 (0.875, 0.0)
 (0.875, 0.25)
 (0.875, 0.5)
 (0.75, 0.625)
 (0.0, 0.875)
 (0.25, 0.875)
 (0.625, 0.75)
 (0.5, 0.875)
```
