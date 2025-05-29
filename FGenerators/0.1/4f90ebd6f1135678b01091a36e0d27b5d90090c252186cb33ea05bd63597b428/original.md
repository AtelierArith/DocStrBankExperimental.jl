```
@yieldfrom foldable
```

Yield items from a `foldable`.  This is usable only inside special contexts such as within [`@fgenerator`](@ref) macro.

## Examples

```jldoctest @yieldfrom
julia> using FGenerators

julia> @fgenerator function flatten2(xs, ys)
           @yieldfrom xs
           @yieldfrom ys
       end;

julia> collect(flatten2(1:2, 11:12))
4-element Array{Int64,1}:
  1
  2
 11
 12
```
