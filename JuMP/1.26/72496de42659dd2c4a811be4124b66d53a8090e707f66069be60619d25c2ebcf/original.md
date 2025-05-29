```
ComplexPlane
```

Complex plane object that can be used to create a complex variable in the [`@variable`](@ref) macro.

## Example

Consider the following example:

```jldoctest
julia> model = Model();

julia> @variable(model, x in ComplexPlane())
real(x) + imag(x) im

julia> all_variables(model)
2-element Vector{VariableRef}:
 real(x)
 imag(x)
```

We see in the output of the last command that two real variables were created. The Julia variable `x` binds to an affine expression in terms of these two variables that parametrize the complex plane.
