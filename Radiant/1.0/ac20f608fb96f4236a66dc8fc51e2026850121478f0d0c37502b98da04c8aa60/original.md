```
Bremsstrahlung
```

Structure used to define parameters for production of multigroup bremsstrahlung cross-sections.

# Mandatory field(s)

  * N/A

# Optional field(s) - with default values

  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Electron,Electron) => ["S"],(Electron,Photon) => ["P"],(Positron,Positron) => ["S"],(Positron,Photon) => ["P"])` : Dictionary of the interaction processes types, of the form (incident particle,outgoing particle) => associated list of interaction type, which values correspond:

      * `(Electron,Electron) => ["S"]` : scattering of incident electron following Bremsstrahlung interaction.
      * `(Electron,Photon) => ["P"]` : produced photon following Bremsstrahlung interaction by incident electron.
      * `(Positron,Positron) => ["S"]` : scattering of incident positron following Bremsstrahlung interaction.
      * `(Positron,Photon) => ["P"]` : produced photon following Bremsstrahlung interaction by incident positron.
  * `angular_scattering_type::String=modified_dipole` : type of angular scattering, which can takes the following values:

      * `angular_scattering_type = modified_dipole` : modified dipôle distribution, based on Poskus (2019) shape functions.
      * `angular_scattering_type = sommerfield` : Sommerfield distribution.
