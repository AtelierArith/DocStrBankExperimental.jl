```
 @NLparameters(model, args...)
```

Create and return multiple nonlinear parameters attached to model `model`, in the same fashion as [`@NLparameter`](@ref) macro.

The model must be the first argument, and multiple parameters can be added on multiple lines wrapped in a `begin ... end` block. Distinct parameters need to be placed on separate lines as in the following example.

The macro returns a tuple containing the parameters that were defined.

!!! compat
    This macro is part of the legacy nonlinear interface. Consider using the new nonlinear interface documented in [Nonlinear Modeling](@ref). In most cases, you can replace a call like

    ```julia
    @NLparameters(model, begin
        p == value
    end)
    ```

    with

    ```julia
    @variables(model, begin
        p in Parameter(value)
    end)
    ```


## Example

```jldoctest
julia> model = Model();

julia> @NLparameters(model, begin
           x == 10
           b == 156
       end);

julia> value(x)
10.0
```
