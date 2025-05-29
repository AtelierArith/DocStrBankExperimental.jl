```
get_var(
    xp::BifrostExperiment,
    snap::Union{<:Integer, AbstractVector{<:Integer}},
    variable::String,
    args...
    ;
    kwargs...
    )
```

Load a `variable` from one or multiple snapshots of `xp`.

# Available variables

The primary variables:

  * "r":  density
  * "px": x-component of momentum
  * "py": y-component of momentum
  * "pz": z-component of momentum
  * "e":  energy

`if params["do_mhd"] == true`

  * "bx": x-component of magnetic field
  * "by": y-component of magnetic field
  * "bz": z-component of magnetic field

auxilliary variables (variables in params["aux"]):

  * "p": pressure
  * "tg": gas temperature   ...

# Optional keyword-arguments

Converts variables to "si" or "cgs" units: `units="si"` or `units="cgs"`.

To load a slice of the variable, give e.g. `slicex=[32, 410]` or `slicey=40:90`

# Example usage:

```{julia}
exp_name = "cb24oi"
exp_dir = "/mn/stornext/d21/RoCS/matsc/3d/run/cb24oi"
snap = 700

xp = BifrostExperiment(expname, expdir)

# Load pressude for the full cube in si units
pressure = get_var(xp, snap, "p"; units="si")

# Load gas density in a slize along the xy-plane in cgs units
rho = get_var(xp, snap, "r"; units="cgs", slicez=[100])
```
