This type is defined to contain all the most relevant properties of a phase, any number of variables can be initialized and defaults will be 0 or empty arrays/strings. Units are selected based on convenience for petrological modelling.

  * `name::String`: Name of the phase
  * `composition::Array{PetroBase.Component}`: Composition of the phase as defined by a 'Component' array
  * `traceelements::Array{PetroBase.TraceElement}`: Concentration of trace elements in the phase
  * `mol::Float64`: Number of moles of the phase present in the system
  * `vol::Float64`: Volume of phase present in the system (J/bar [m^3/10^5])
  * `mass::Float64`: Total mass of the phase present in the system (g)
  * `ρ::Float64`: Density (kg/m^3)
  * `molarmass::Float64`: Molar mass (g/mol)
  * `G::Float64`: Gibbs free energy (J/mol)
  * `H::Float64`: Enthalpy (J/mol)
  * `S::Float64`: Entropy (J/mol)
  * `Cp::Float64`: Heat capacity (J/K·mol)
  * `Vmol::Float64`: Molar volume (J/bar·mol)
  * `Cp_Cv::Float64`: Cp/Cv (heat capacity ratio)
  * `α::Float64`: Thermal expansion coefficient(1/K)
  * `β::Float64`: Compressibility (1/bar)
