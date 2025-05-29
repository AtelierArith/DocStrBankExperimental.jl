Structure containing all the data required for the evaluation of the power flows and angles, as well as these ones.

# Arguments:

  * `bus_lookup::Dict{Int, Int}`:       dictionary linking the system's bus number with the rows of either       "power*network*matrix" or "aux*network*matrix".
  * `branch_lookup::Dict{String, Int}`:       dictionary linking the branch name with the column name of either the       "power*network*matrix" or "aux*network*matrix".
  * `bus_activepower_injection::Matrix{Float64}`:       "(b, t)" matrix containing the bus active power injection. b: number of       buses, t: number of time period.
  * `bus_reactivepower_injection::Matrix{Float64}`:       "(b, t)" matrix containing the bus reactive power injection. b: number       of buses, t: number of time period.
  * `bus_activepower_withdrawals::Matrix{Float64}`:       "(b, t)" matrix containing the bus reactive power withdrawals. b:       number of buses, t: number of time period.
  * `bus_reactivepower_withdrawals::Matrix{Float64}`:       "(b, t)" matrix containing the bus reactive power withdrawals. b:       number of buses, t: number of time period.
  * `bus_reactivepower_bounds::Matrix{Float64}`:       "(b, t)" matrix containing upper and lower bounds for the reactive supply at each       bus at each time period.
  * `bus_type::Matrix{PSY.ACBusTypes}`:       "(b, t)" matrix containing type of buses present in the system, ordered       according to "bus_lookup," at each time period.
  * `bus_magnitude::Matrix{Float64}`:       "(b, t)" matrix containing the bus magnitudes, ordered according to       "bus_lookup". b: number of buses, t: number of time period.
  * `bus_angles::Matrix{Float64}`:       "(b, t)" matrix containing the bus angles, ordered according to       "bus_lookup". b: number of buses, t: number of time period.
  * `branch_activepower_flow_from_to::Matrix{Float64}`:       "(br, t)" matrix containing the active power flows measured at the `from` bus,       ordered according to "branch_lookup". br: number of branches, t: number of time       period.
  * `branch_reactivepower_flow_from_to::Matrix{Float64}`:       "(br, t)" matrix containing the reactive power flows measured at the `from` bus,       ordered according to "branch_lookup". br: number of branches, t: number of time       period.
  * `branch_activepower_flow_to_from::Matrix{Float64}`:       "(br, t)" matrix containing the active power flows measured at the `to` bus, ordered       according to "branch_lookup". br: number of branches, t: number of time period.
  * `branch_reactivepower_flow_to_from::Matrix{Float64}`:       "(br, t)" matrix containing the reactive power flows measured at the `to` bus,       ordered according to "branch_lookup". br: number of branches, t: number of time       period.
  * `timestep_map::Dict{Int, S}`:       dictonary mapping the number of the time periods (corresponding to the       column number of the previosly mentioned matrices) and their names.
  * `valid_ix::Vector{Int}`:       vector containing the indeces of not slack buses
  * `power_network_matrix::M`:       matrix used for the evaluation of either the power flows or bus angles,       depending on the method considered.
  * `aux_network_matrix::N`:       matrix used for the evaluation of either the power flows or bus angles,       depending on the method considered.
  * `neighbors::Vector{Set{Int}}`: Vector with the sets of adjacent buses.
