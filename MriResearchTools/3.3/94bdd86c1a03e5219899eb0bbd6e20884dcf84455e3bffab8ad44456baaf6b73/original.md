```
readmag(filename; rescale=false, keyargs...)
```

Reads the NIfTI magnitude with sanity checking and optional rescaling to [0;1].

# Examples

```julia-repl
julia> mag = readmag("mag.nii")
```

### Optional keyargs are forwarded to `niread`:

Base.Docs.DocStr(svec("    niread(file; mmap=false, mode=\"r\")\n\nRead a NIfTI file to a NIVolume. Set `mmap=true` to memory map the volume.\n"), nothing, Dict{Symbol, Any}(:typesig => Tuple{AbstractString}, :module => NIfTI, :linenumber => 234, :binding => NIfTI.niread, :path => "/home/terasaki/.julia/packages/NIfTI/ytzbJ/src/NIfTI.jl"))
