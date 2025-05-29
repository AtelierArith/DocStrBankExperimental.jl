Inelastic_Collision

Structure used to define parameters for production of multigroup inelastic collisional cross-sections.

# Mandatory field(s)

  * N/A

# Optional field(s) - with default values

  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Positron,Positron) => ["S"],(Positron,Electron) => ["P"],(Electron,Electron) => ["S","P"])` : Dictionary of the interaction processes types, of the form (incident particle,outgoing particle) => associated list of interaction type, which values correspond:

      * `(Positron,Positron) => ["S"]` : scattering of incident positrons
      * `(Electron,Electron) => ["S"]` : scattering of incident electrons
      * `(Positron,Electron) => ["P"]` : production of electrons by incident positrons
      * `(Electron,Electron) => ["P"]` : production of electrons by incident electrons
