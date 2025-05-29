```
component(v::PVector{T,N}, i)::PVector{T,1}
```

$$
v ∈ P(ℂ^n₁) × ... × P(ℂ^nⱼ)
$$

の$i$-番目の成分を取得します。

## 例

```julia
julia> v = PVector([1, 2, 3]);
julia> w = PVector([4, 5]);
julia> v × w
[1 : 2 : 3] × [4 : 5]
julia> component(v × w, 1)
[1 : 2 : 3]
# 代わりにインデックスを使うこともできます
julia> (v × w)[1,:]
[1 : 2 : 3]
```
