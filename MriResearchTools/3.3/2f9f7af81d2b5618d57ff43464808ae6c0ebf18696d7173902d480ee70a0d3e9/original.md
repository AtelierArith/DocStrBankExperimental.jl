```
mcpc3ds(phase, mag; TEs, keyargs...)

mcpc3ds(compl; TEs, keyargs...)

mcpc3ds(phase; TEs, keyargs...)
```

Perform MCPC-3D-S coil combination and phase offset removal on 4D (multi-echo) and 5D (multi-echo, uncombined) input.

## Optional Keyword Arguments

  * `echoes`: only use the defined echoes. default: `echoes=[1,2]`
  * `sigma`: smoothing parameter for phase offsets. default: `sigma=[10,10,5]`
  * `bipolar_correction`: removes linear phase artefact. default: `bipolar_correction=false`
  * `po`: phase offsets are stored in this array. Can be used to retrieve phase offsets or work with memory mapping.

# Examples

```julia-repl
julia> phase = readphase("phase5D.nii")
julia> mag = readmag("mag5D.nii")
julia> combined = mcpc3ds(phase, mag; TEs=[4,8,12])
```

For very large files that don't fit into memory, the uncombined data can be processed with memory mapped to disk:

```julia-repl
julia> phase = readphase("phase5D.nii"; mmap=true)
julia> mag = readmag("mag5D.nii"; mmap=true)
julia> po_size = (size(phase)[1:3]..., size(phase,5))
julia> po = write_emptynii(po_size, "po.nii")
julia> combined = mcpc3ds(phase, mag; TEs=[4,8,12], po)
```
