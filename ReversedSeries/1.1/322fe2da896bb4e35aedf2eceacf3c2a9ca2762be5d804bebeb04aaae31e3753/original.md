```julia
struct Reversed{T<:AbstractArray}
```

  * `A::AbstractArray`

This presents a reversed view of anything array-like.

Credit: [@simsurace](https://discourse.julialang.org/t/how-to-create-a-reversed-view-that-allows-for-growing-arrays/96148/2)

# Example

```julia-repl
julia> a = [1, 2, 3]
julia> r = Reversed(a)
julia> r[1]
3
julia> r[3]
1
julia> a[end] == r[1]
true
```
