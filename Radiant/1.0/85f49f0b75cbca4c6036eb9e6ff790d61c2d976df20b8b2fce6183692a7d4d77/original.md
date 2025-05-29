Cross_Sections

Structure used to define the parameters to extract or build a multigroup cross-sections library.

# Mandatory field(s)

  * `source::String` : source of the cross-sections.
  * `materials::Vector{Material}` : material list.
  * **if `source = "fmac-m"`**

      * `file::String` : file containing cross-sections data.
  * **if `source = "physics-models"`**

      * `particles::Vector{String}` : particle list.
      * `energy::Float64` : midpoint energy of the highest energy group [in MeV].
      * `number_of_groups::Int64` : number of energy groups.
      * `group_structure::String="log"` : type of group discretization.
      * `legendre_order::Int64` : maximum order of the angular Legendre moments of the differential cross-sections.
      * `interactions::Vector{Interaction}` : list of interaction.
  * ** if `source = "custom"`**

      * `particles::Vector{String}` : particle list.

# Optional field(s) - with default values

  * **if `source = "physics-models"`**

      * `cutoff::Float64 = 0.001` : lower energy bound of the lowest energy group (cutoff energy) [in MeV].
  * ** if `source = "custom"`**

      * `custom_absorption::Vector{Real}` : absorption cross-sections per material.
      * `custom_scattering::Vector{Real}` : scattering (isotropic) cross-sections per material.
