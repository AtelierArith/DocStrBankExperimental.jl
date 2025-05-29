```
Elastic_Collision
```

Structure used to define parameters for production of multigroup elastic collision cross-sections.

# Mandatory field(s)

  * N/A

# Optional field(s) - with default values

  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Electron,Electron) => ["S"],(Positron,Positron) => ["S"])` : Dictionary of the interaction processes types, of the form (incident particle,outgoing particle) => associated list of interaction type, which values correspond:

      * `(Electron,Electron) => ["S"]` : elastic interaction of electrons.
      * `(Positron,Positron) => ["S"]` : elastic interaction of positrons.
