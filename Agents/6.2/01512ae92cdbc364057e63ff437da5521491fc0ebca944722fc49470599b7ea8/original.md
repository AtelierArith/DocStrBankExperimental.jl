```
@multiagent YourAgentType(AgentTypesToMerge...) [<: OptionalSupertype]
```

Define multiple agent "subtypes", which are variants of a unique type `YourAgentType`. This means that all "subtypes" are enclosed in the overarching type. Then, You cannot distinguish them on the basis of `typeof`, but need to use instead the `variantof` function. The `allvariants` function for a convenient way to obtain all variants types.

See the [Tutorial](@ref) or the [performance comparison versus `Union` types](@ref multi_vs_union) for why it is often better to use `@multiagent` than making multiple agent types.

`@multiagent` is based on LightSumTypes.jl.

## Examples

Let's say you have this definition:

```
@agent struct Wolf
    energy::Float64 = 0.5
    ground_speed::Float64
    const fur_color::Symbol
end
@agent struct Hawk{T}
    energy::Float64 = 0.1
    ground_speed::Float64
    flight_speed::T
end

@multiagent Animal(Wolf, Hawk{Float64})
```

Then you can create `Wolf` and `Hawk` agents like so

```
hawk_1 = (Animal ∘ Hawk)(1, (1, 1), 1.0, 2.0, 3)
hawk_2 = (Animal ∘ Hawk)(; id = 2, pos = (1, 2), ground_speed = 2.3, flight_speed = 2)
wolf_1 = (Animal ∘ Wolf)(3, (2, 2), 2.0, 3.0, :black)
wolf_2 = (Animal ∘ Wolf)(; id = 4, pos = (2, 1), ground_speed = 2.0, fur_color = :white)
```

The way to retrieve the variant of the agent is through the function `variantof` e.g.

```
variantof(hawk_1) # Hawk
variantof(wolf_2) # Wolf
```

You can also access the enclosed variant instance with the variant `function`

```
variant(hawk_1) # Hawk(1, (1, 1), 1.0, 2.0, 3.0)
variant(wolf_1) # Wolf(3, (2, 2), 2.0, 3.0, :black)
```

See the [Rabbit-Fox-Hawk example](@ref rabbit_fox_hawk) to see how to use this macro in a model.
