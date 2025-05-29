```julia
assemble!(
    assembler::FiniteElementContainers.DynamicAssembler,
    dof::FiniteElementContainers.DofManager,
    fspace::FiniteElementContainers.FunctionSpace,
    X,
    U,
    block_id,
    residual_func,
    tangent_func,
    mass_func
)

```

Simple method for assembling in serial
