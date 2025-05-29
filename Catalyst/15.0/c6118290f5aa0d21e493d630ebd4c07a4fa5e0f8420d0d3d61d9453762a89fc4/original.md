```
@reaction_network
```

Macro for generating chemical reaction network models (Catalyst `ReactionSystem`s). See the ([DSL introduction](https://docs.sciml.ai/Catalyst/stable/model_creation/dsl_basics/) and [advantage usage](https://docs.sciml.ai/Catalyst/stable/model_creation/dsl_advanced/)) sections of the Catalyst documentation for more details on the domain-specific language (DSL) that the macro implements. The macro's output (a `ReactionSystem` structure) is central to Catalyst and its functionality. How to e.g. simulate these is described in the [Catalyst documentation](https://docs.sciml.ai/Catalyst/stable/).

Returns:

  * A Catalyst `ReactionSystem`, i.e. a symbolic model for the reaction network. The returned

system is marked `complete`. To obtain a `ReactionSystem` that is not marked complete, for example to then use in compositional modelling, see the otherwise equivalent `@network_component` macro.

Examples: Here we create a basic SIR model. It contains two reactions (infection and recovery):

```julia
sir_model = @reaction_network begin
    c1, S + I --> 2I
    c2, I --> R
end
```

Next, we create a self-activation loop. Here, a single component (`X`) activates its own production with a Michaelis-Menten function:

```julia
sa_loop = @reaction_network begin
    mm(X,v,K), 0 --> X
    d, X --> 0
end
```

This model also contains production and degradation reactions, where `0` denotes that there are either no substrates or no products in a reaction.

Options: In addition to reactions, the macro also supports "option" inputs (permitting e.g. the addition of observables). Each option is designated by a tag starting with a `@` followed by its input. A list of options can be found [here](https://docs.sciml.ai/Catalyst/stable/api/#api_dsl_options).
