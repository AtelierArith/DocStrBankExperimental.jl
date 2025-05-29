```
Node
```

Abstract type from which every node in a graph should inherit. This allows using the graph construction DSL.

# Example

```jldoctest
julia> struct bar <: Node
           x::Int
       end;

julia> b1 = bar(1);

julia> b2 = bar(2);

julia> b1 + b2;
```
