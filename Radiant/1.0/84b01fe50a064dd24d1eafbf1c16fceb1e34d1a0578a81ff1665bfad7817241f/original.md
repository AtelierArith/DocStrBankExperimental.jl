```
Compton
```

Structure used to define parameters for production of multigroup Compton cross-sections.

# Mandatory field(s)

  * N/A

# Optional field(s) - with default values

  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Photon,Photon) => ["S"],(Photon,Electron) => ["P"])` : Dictionary of the interaction processes types, of the form (incident particle,outgoing particle) => associated list of interaction type, which values correspond:

      * `(Photon,Photon) => ["S"]` : scattering of incident photon following Compton interaction.
      * `(Photon,Electron) => ["P"]` : produced electron following Compton interaction.
