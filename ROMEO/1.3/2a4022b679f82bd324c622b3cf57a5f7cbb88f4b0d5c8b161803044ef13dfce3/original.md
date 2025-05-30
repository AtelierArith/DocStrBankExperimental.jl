```
voxelquality(phase::AbstractArray; keyargs...)
```

Calculates a quality for each voxel. The voxel quality can be used to create a mask. The quality range is [0;1]

# Examples

```julia-repl
julia> qmap = voxelquality(phase_3echo; TEs=[1,2,3]);
julia> mask = robustmask(qmap);
```

Takes the same inputs as `romeo`/`unwrap`:

See also [`unwrap`](@ref)
