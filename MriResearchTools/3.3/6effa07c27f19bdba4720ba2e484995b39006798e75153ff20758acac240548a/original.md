```
readphase(filename; rescale=true, fix_ge=false, keyargs...)
```

Reads the NIfTI phase with sanity checking and optional rescaling to [-π;π]. Warning for GE: `fix_ge=true` is probably required and will add pi to every second slice.

# Examples

```julia-repl
julia> phase = readphase("phase.nii")
```

### Optional keyargs are forwarded to `niread`:

Base.Docs.DocStr(svec("    niread(file; mmap=false, mode=\"r\")\n\nRead a NIfTI file to a NIVolume. Set `mmap=true` to memory map the volume.\n"), nothing, Dict{Symbol, Any}(:typesig => Tuple{AbstractString}, :module => NIfTI, :linenumber => 234, :binding => NIfTI.niread, :path => "/home/terasaki/.julia/packages/NIfTI/ytzbJ/src/NIfTI.jl"))
