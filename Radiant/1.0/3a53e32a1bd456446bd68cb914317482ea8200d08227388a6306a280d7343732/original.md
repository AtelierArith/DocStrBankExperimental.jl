```
Annihilation
```

Structure used to define parameters for production of multigroup annihilation cross-sections.

# Mandatory field(s)

  * N/A

# Optional field(s) - with default values

  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Positron,Positron) => ["A"],(Positron,Photon) => ["P","P_inel","P_brems"],(Photon,Photon) => ["P_pp"])` : Dictionary of the interaction processes types, of the form (incident particle,outgoing particle) => associated list of interaction type, which values correspond:

      * `(Positron,Positron) => ["A"]` : absorption of the incoming positron.
      * `(Positron,Photon) => ["P"]` : production of the two photons following annihilation.
      * `(Positron,Photon) => ["P_inel"]` : production of annihilation photons from inelastic collisional positrons absorption following scattering under the cutoff energy.
      * `(Positron,Photon) => ["P_brems"]` : production of annihilation photons from Bremsstrahlung positrons absorption following scattering under the cutoff energy.
      * `(Photon,Photon) => ["P_pp"]` : production of annihilation photons from absorption of positrons following their production under the cutoff energy.
