```
Pair_Production
```

Structure used to define parameters for production of multigroup pair production cross-sections.

# Mandatory field(s)

  * N/A

# Optional field(s) - with default values

  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Photon,Photon) => ["A"],(Photon,Electron) => ["P"],(Photon,Positron) => ["P"])` : Dictionary of the interaction processes types, of the form (incident particle,outgoing particle) => associated list of interaction type, which values correspond:

      * `(Photon,Photon) => ["A"]` : absorption of incoming photon.
      * `(Photon,Electron) => ["P"]` : produced electron.
      * `(Photon,Positron) => ["P"]` : produced positron.
  * `angular_scattering_type::String=modified_dipole` : type of angular scattering, which can takes the following values:

      * `angular_scattering_type = modified_dipole` : modified dipôle distribution, based on Poskus (2019) shape functions.
      * `angular_scattering_type = sommerfield` : Sommerfield distribution.
