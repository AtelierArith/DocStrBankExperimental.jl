```
push!(ir, x)
```

Append the statement or expression `x` to the IR or block `ir`, returning the new variable. See also [`pushfirst!`](@ref), [`insert!`](@ref).

```
julia> ir = IR();

julia> x = argument!(ir)
%1

julia> push!(ir, xcall(:*, x, x))
%2

julia> ir
1: (%1)
  %2 = %1 * %1
```
