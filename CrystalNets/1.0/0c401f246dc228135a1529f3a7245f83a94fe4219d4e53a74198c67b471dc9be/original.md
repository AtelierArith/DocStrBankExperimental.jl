```
CrystalNets.jl
```

Module for automatic recognition of crystal net topologies. To use as an executable, run the source file in a shell:

```bash
julia --project=/path/to/CrystalNets/ /path/to/CrystalNets/src/CrystalNets.jl
```

Otherwise, as a module, to try to recognize the net underlying a crystal given in a chemical file format called FILE, the entry point is the following execution:

```julia
julia> using CrystalNets

julia> determine_topology(FILE)
```

See the documentation at https://coudertlab.github.io/CrystalNets.jl/ for further instructions on on the use of CrystalNets.jl, and how to do a full installation to reduce latency at startup.
