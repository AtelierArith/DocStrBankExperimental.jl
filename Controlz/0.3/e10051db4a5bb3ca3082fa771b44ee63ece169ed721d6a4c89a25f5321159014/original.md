```
root_locus(g_ol, max_mag_Kc=10.0, nb_pts=500, savename=nothing, legend_pos=:rt)
```

visualize the root locus plot of an open-loop transfer function `g_ol`.

# Arguments

  * `g_ol::TransferFunction`: the open-loop transfer function of the closed loop system
  * `max_mag_Kc::Float64=10.0`: the maximum magnitude by which the gain of `g_ol` is    scaled in order to see the roots traversing the plane
  * `nb_pts::Int=500`: the number of gains to explore. increase for higher resolution.
  * `legend_pos::Symbol`: Makie command for where to place legend

# returns

a `CairoMakie.jl` `Figure` object for further modification.
