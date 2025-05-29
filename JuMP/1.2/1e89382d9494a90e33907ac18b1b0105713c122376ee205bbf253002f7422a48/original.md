```
 @NLparameters(model, args...)
```

Create and return multiple nonlinear parameters attached to model `model`, in the same fashion as [`@NLparameter`](@ref) macro.

The model must be the first argument, and multiple parameters can be added on multiple lines wrapped in a `begin ... end` block. Distinct parameters need to be placed on separate lines as in the following example.

The macro returns a tuple containing the parameters that were defined.

# Example

```jldoctest; setup=:(using JuMP)
model = Model()
@NLparameters(model, begin
    x == 10
    b == 156
end)
value(x)

# output
10.0
```

```

```
