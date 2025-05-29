```
@reaction_network
```

Generates a [`ReactionSystem`](@ref dsl_description) that encodes a chemical reaction network.

See [The Reaction DSL](@ref dsl_description) documentation for details on parameters to the macro.

Examples:

```julia
# a basic SIR model, with name SIR
sir_model = @reaction_network SIR begin
    c1, s + i --> 2i
    c2, i --> r
end

# a basic SIR model, with random generated name
sir_model = @reaction_network begin
    c1, s + i --> 2i
    c2, i --> r
end

# an empty network with name empty
emptyrn = @reaction_network empty

# an empty network with random generated name
emptyrn = @reaction_network
```

ReactionSystems generated through `@reaction_network` are complete.
