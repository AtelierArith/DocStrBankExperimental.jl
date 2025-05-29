```
Relaxation
```

Structure used to define parameters for relaxation cascades (florescence and Auger electron production)

# Mandatory field(s)

  * N/A

# Optional field(s) - with default values

  * `ηmin::Float64 = 0.001` : minimum probability of the production of specific relaxation  particle production following electron cascades.
  * `interaction_types::Dict{Tuple{DataType,DataType},Vector{String}} = Dict((Photon,Electron) => ["P"],(Electron,Electron) => ["P"],(Positron,Electron) => ["P"],(Photon,Photon) => ["P"],(Electron,Photon) => ["P"],(Positron,Photon) => ["P"])` : Dictionary of the interaction processes types, of the form (incident particle,outgoing particle) => associated list of interaction type, which values correspond:

      * `(Photon,Electron) => ["P"]` : production of Auger electron following incident photon ionization of subshells (by photoelectric effect).
      * `(Electron,Electron) => ["P"]` : production of Auger electron following incident electrons ionization of subshells (by Møller interaction).
      * `(Positron,Electron) => ["P"]` : production of Auger electron following incident positrons ionization of subshells (by Bhabha interaction).
      * `(Photon,Photon) => ["P"]` : production of fluorescence following incident photon ionization of subshells (by photoelectric effect).
      * `(Electron,Photon) => ["P"]` : production of fluorescence following incident electrons ionization of subshells (by Møller interaction).
      * `(Positron,Photon) => ["P"]` : production of fluorescence following incident positrons ionization of subshells (by Bhabha interaction).
