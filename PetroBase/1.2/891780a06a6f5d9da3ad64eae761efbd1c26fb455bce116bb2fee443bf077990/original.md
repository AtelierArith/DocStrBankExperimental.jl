This type is defined to contain all the most relevant properties of a petrological system, any number of variables can be initialized  and defaults will be 0 or empty arrays/strings. Units are selected based on convenience for petrological modelling.

  * `composition::Array{PetroBase.Component}`: Composition of the system as defined by a 'Component' array
  * `phases::Array{PetroBase.Phase}`: Phases within the system
  * `traceelements::Array{PetroBase.TraceElement}`: Concentration of trace elements in the system
  * `mol::Float64`: Total moles of all components in the system
  * `vol::Float64`: Total volume of all phases in the system(J/bar [m^3/10^5])
  * `mass::Float64`: Total mass of the system(g)
  * `ρ::Float64`: Density of the system (kg/m^3)
  * `molarmass::Float64`: Molar mass of the system (kg/m^3)
  * `G::Float64`: Gibbs free energy (J/mol)
  * `H::Float64`: Enthalpy (J/mol)
  * `S::Float64`: Entropy (J/K·mol)
  * `Cp::Float64`: Heat capacity (J/K·mol)
  * `Vmol::Float64`: Molar volume (J/bar·mol)
  * `Cp_Cv::Float64`: Cp/Cv (heat capacity ratio)
  * `α::Float64`: Thermal expansion coefficient(1/K)
  * `β::Float64`: Compressibility (1/bar)
