```
@sample(def)
```

Define the sample operaton inside a @sampler block, using the syntax

```julia
@sample begin
    ...
    return sampled_scenario
end
```

The sampler object is referenced through the reserved keyword `sampler`, from which any internals can be accessed.
