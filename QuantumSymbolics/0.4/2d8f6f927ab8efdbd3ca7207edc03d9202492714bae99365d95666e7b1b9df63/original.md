Vectorization of a symbolic operator.

```jldoctest
julia> @op A; @op B;

julia> vec(A)
|A⟩⟩

julia> vec(A+B)
|A⟩⟩+|B⟩⟩
```
