```
DcdFile
```

Handle to a dcd File. Opening in read mode reads the header  and stores the offsets to the frames for fast random access.     

# Useful fields, all initialized on opening in read mode.

  * natoms::Int
  * nframes::Int
  * time::Vector{Float32}(nframes)

# Constructor

```
DcdFile(name::AbstractString, mode::AbstractString)
```

mode is the usual string r,w,a
