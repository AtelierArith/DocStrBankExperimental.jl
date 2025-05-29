```
createMIP(S::AbstractArray{<:Number,3}, d=7)
```

Creates minimum intensity projection of `S` over `d` slices.

# Examples

```julia-repl
julia> TEs = [4,8,12]
julia> data = Data(mag, phase, header(mag), TEs);
julia> swi = calculateSWI(data);
julia> mip = createMIP(swi);
```

See also [`createIntensityProjection`](@ref)
