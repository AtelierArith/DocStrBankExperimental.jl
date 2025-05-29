```
export_variants(T)
```

Export all variants types into the module the function it is called into.

## Example

```julia
julia> @sum_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> AB'.A(1)
AB'.A(1)

julia> export_variants(AB)

julia> A(1) # now this also works
AB'.A(1)
```
