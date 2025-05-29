```
kindof(instance)
```

Return a symbol representing the conceptual type of an instance:

```julia
julia> @compact_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> a = A(1);

julia> kindof(a)
:A
```
