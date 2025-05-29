```
examples_dir()
```

Return the directory where the example files provided with TrixiParticles.jl are located. If TrixiParticles is installed as a regular package (with `]add TrixiParticles`), these files are read-only and should *not* be modified. To find out which files are available, use, e.g., `readdir`.

Copied from [Trixi.jl](https://github.com/trixi-framework/Trixi.jl).

# Examples

```jldoctest; output = false, filter = r"\d+-element Vector.*"s
readdir(examples_dir())

# output
7-element Vector{String}:
 [...] (the rest is ignored by filter condition)
```
