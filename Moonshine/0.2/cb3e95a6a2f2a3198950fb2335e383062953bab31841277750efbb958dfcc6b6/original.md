```
ancestral_mask!(η, reference, x; ωs_buf = Set{Ω}(), wipe = true)
```

Mask non ancestral positions to 0. If `wipe = true`, all markers in `η` will be initialized to 0.

# Methods

```julia
ancestral_mask!(η, arg, e; wipe)
```

defined at [`packages/Moonshine/7JVTP/src/Arg/Arg.jl:203`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Arg/Arg.jl).

```julia
ancestral_mask!(h, arg, v; buffer, wipe)
```

defined at [`packages/Moonshine/7JVTP/src/Arg/Arg.jl:206`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Arg/Arg.jl).

```julia
ancestral_mask!(η, genealogy, x; wipe)
```

defined at [`packages/Moonshine/7JVTP/src/Genealogy.jl:408`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl).

```julia
ancestral_mask!(v, sample, ω; wipe)
```

defined at [`packages/Moonshine/7JVTP/src/Sample.jl:300`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Sample.jl).

```julia
ancestral_mask!(η, sample, ω; wipe)
```

defined at [`packages/Moonshine/7JVTP/src/Sample.jl:310`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Sample.jl).

```julia
ancestral_mask!(η, sample, ωs; wipe)
```

defined at [`packages/Moonshine/7JVTP/src/Sample.jl:316`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Sample.jl).

```julia
ancestral_mask!(η, sample, pos; wipe)
```

defined at [`packages/Moonshine/7JVTP/src/Sample.jl:329`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Sample.jl).
