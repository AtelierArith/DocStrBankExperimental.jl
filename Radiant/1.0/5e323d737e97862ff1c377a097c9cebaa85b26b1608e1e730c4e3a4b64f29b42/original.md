```
Photoelectric
```

Structure used to define parameters for production of multigroup photoelectric cross-sections.

# Mandatory field(s)

  * N/A

# Optional field(s) - with default values

  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Photon,Photon) => ["A"],(Photon,Electron) => ["P"])` : Dictionary of the interaction processes types, of the form (incident particle,outgoing particle) => associated list of interaction type, which values correspond:

      * `(Photon,Photon) => ["A"]` : absorption of incoming photon.
      * `(Photon,Electron) => ["P"]` : produced photo-electron.
