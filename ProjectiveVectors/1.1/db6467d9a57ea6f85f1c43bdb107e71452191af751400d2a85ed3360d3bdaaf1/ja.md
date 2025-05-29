```
components(v::PVector{T,N})::NTuple{N, PVector{T, 1}}
```

要素 $v ∈ P(ℂ^n₁) × ... × P(ℂ^nⱼ)$ を $(v₁, …, vⱼ) = v$ に分解します。

## 例

```julia
julia> v = PVector([1, 2, 3]);
julia> w = PVector([4, 5]);
julia> v × w
[1 : 2 : 3] × [4 : 5]
julia> components(v × w) == (v, w)
true
```
