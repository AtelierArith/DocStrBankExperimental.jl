```
allkinds(type)
```

Return a `Tuple` containing all kinds associated with the overarching  type defined with `@sum_structs`

```julia
julia> @sum_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> allkinds(AB)
(:A, :B)
```
