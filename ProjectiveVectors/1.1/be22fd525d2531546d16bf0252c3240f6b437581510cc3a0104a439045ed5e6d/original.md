```
component(v::PVector{T,N}, i)::PVector{T,1}
```

Obtain the `i`-th component of $v ∈ P(ℂ^n₁) × ... × P(ℂ^nⱼ)$.

## Example

```julia
julia> v = PVector([1, 2, 3]);
julia> w = PVector([4, 5]);
julia> v × w
[1 : 2 : 3] × [4 : 5]
julia> component(v × w, 1)
[1 : 2 : 3]
# alternative you can also indexing
julia> (v × w)[1,:]
[1 : 2 : 3]
```
