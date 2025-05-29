```
cobra(eq, surfs, nwells, θs, ζs, mode=1, geom_input=true, tokamak_input=false, lscreen=true)
```

Calculates ballooning equilibrium based off of the CobraVmec code. Originally converted from fortran to Julia by Sanket Patil, rewritten by Aaron Bader

# Arguments

  * `eq::E`: A Vmec or DESC (eventually) equilibrium
  * `slist::Vector{Int64}`: list of s values
  * `nwells::Int64`: Number of helical wells to include

# Optional inputs

  * `θs::Vector{Float64}`: Vector of starting θ values (in radians)
  * `ζs::Vector{Float64}`: Vector of starting ζ values (in radians normalized to field periods)
  * `mode::Int64`: mode number, 1 is the most unstable mode
  * `geom_input::Bool`: Flag, default true
  * `tokamak_input::Bool`: Flag, default false, not sure we'll ever use this
  * `lscreen::Bool`: Flag, output to screen, default true
