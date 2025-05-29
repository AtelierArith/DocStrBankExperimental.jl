```
savereplicates(f, b::MixedModelFitCollection)
```

Save the replicates associated with a [`MixedModelFitCollection`](@ref), e.g. [`MixedModelBootstrap`](@ref) as an Arrow file.

See also [`restorereplicates`](@ref), [`saveoptsum`](@ref)

!!! note
    **Only** the replicates are saved, not the entire contents of the `MixedModelFitCollection`. `restorereplicates` requires a model compatible with the bootstrap to restore the full object.

