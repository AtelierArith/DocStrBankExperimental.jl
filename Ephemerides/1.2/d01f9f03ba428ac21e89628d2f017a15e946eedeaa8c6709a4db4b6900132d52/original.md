```
EphemerisProvider(file::String)
EphemerisProvider(files::Vector{String})
```

Create an `EphemerisProvider` instance by loading a single or multiple binary ephemeris  kernel files specified by `files`. Currently, only NAIF Double precision Array File (DAF) kernels (i.e., SPK and PCK) are accepted.

### Example

```julia-repl
julia> eph = EphemerisProvider("PATH_TO_KERNEL")
EphemerisProvider([...])

julia> eph = EphemerisProvider(["PATH_TO_KERNEL_1", "PATH_TO_KERNEL_2"])
EphemerisProvider([])
```
