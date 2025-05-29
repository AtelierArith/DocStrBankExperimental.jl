```julia
check_consistency(
    state::ModelingToolkit.TransformationState,
    orig_inputs;
    nothrow
) -> Bool

```

Check the consistency of `state`, given the inputs `orig_inputs`. If `nothrow == false`, throws an error if the system is under-/over-determined or singular. In this case, if the function returns it will return `true`. If `nothrow == true`, it will return `false` instead of throwing an error. The singular case will print a warning.
