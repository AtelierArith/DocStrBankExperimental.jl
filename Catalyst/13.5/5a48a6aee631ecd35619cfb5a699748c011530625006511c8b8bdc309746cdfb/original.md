```
@add_reactions
```

Adds the reactions declared to a preexisting [`ReactionSystem`](@ref). Note, mutates the original network.

Notes:

  * To instead generate a new network by combining two existing networks use `ModelingToolkit.extend`.

Example:

```julia
rn = @reaction_network begin
    @parameters G
    π, 2*A --> B
    end

# add this reaction into rn
@add_reactions rn begin
    k*A, C --> D
end
```
