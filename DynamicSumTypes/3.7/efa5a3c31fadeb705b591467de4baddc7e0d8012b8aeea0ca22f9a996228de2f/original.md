```
variant_constructor(instance)
```

Return the constructor of an instance in a more efficient way than doing `typeof(inst)'[kindof(inst)]`:

```julia
julia> @sum_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> a = AB'.A(1)
AB'.A(1)

julia> typeof(a)'[kindof(a)]
AB'.A

julia> variant_constructor(a)
AB'.A
```
