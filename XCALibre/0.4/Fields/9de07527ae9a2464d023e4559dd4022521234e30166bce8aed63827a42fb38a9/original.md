```
function initialise!(field, value) # dummy function for documentation
    # Assign `value` to field in-place
    nothing
end
```

This function will set the given `field` to the `value` provided in-place. Useful for initialising fields prior to running a simulation.

# Input arguments

  * `field` specifies the field to be initialised. The field must be either a `AbractScalarField` or `AbstractVectorField`
  * `value` defines the value to be set. This should be a scalar or vector (3 components) depending on the field to be modified e.g. for an `AbstractVectorField` we can specify as `value=[10,0,0]`

Note: in most cases the fields to be modified are stored within a physics model i.e. a `Physics` object. Thus, the argument `value` must fully qualify the model. For example, if we have created a `Physics` model named `mymodel` to set the velocity field, `U`, we would set the argument `field` to `mymodel.momentum.U`. See the example below.

# Example

```julia
initialise!(mymodel.momentum.U, [2.5, 0, 0])
initialise!(mymodel.momentum.p, 1.25)
```
