```
GraphNode{T} <: AbstractExpressionNode{T}
```

Exactly the same as [`Node{T}`](@ref), but with the assumption that some nodes will be shared. All copies of this graph-like structure will be performed with this assumption, to preserve structure of the graph.

# Examples

```julia
julia> operators = OperatorEnum(;
           binary_operators=[+, -, *], unary_operators=[cos, sin]
        );

julia> x = GraphNode(feature=1)
x1

julia> y = sin(x) + x
sin(x1) + {x1}

julia> cos(y) * y
cos(sin(x1) + {x1}) * {(sin(x1) + {x1})}
```

Note how the `{}` indicates a node is shared, and this is the same node as seen earlier in the string.

This has the same constructors as [`Node{T}`](@ref). Shared nodes are created simply by using the same node in multiple places when constructing or setting properties.
