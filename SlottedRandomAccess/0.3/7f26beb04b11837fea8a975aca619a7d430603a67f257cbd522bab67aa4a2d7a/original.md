```julia
struct PLR_SimulationParameters{RA, F}
```

Type storing the parameters to be used for a PLR simulation.

# Fields

  * `scheme::Any`: The specific RA scheme
  * `poisson::Bool`: Flag specifying whether the simulation should assume poisson or constant traffic
  * `coderate::Float64`: The coderate of the packets sent by the users
  * `M::Int64`: The modulation cardinality of the packets sent by the users
  * `power_dist::Any`: Distribution used to generate the random power values
  * `power_strategy::SlottedRandomAccess.ReplicaPowerStrategy`: The strategy to assign power to the replicas of a given packet. Must be a valid value of [`ReplicaPowerStrategy`](@ref) enum type.
  * `max_simulated_frames::Int64`: The number of RA frames to simulate for each Load point
  * `nslots::Int64`: The number of slots in each RA frame
  * `plr_func::Any`: The function used to compute the PLR for a given packet as a function of its equivalent Eb/N0
  * `noise_variance::Float64`: The variance of the noise, assumed as N0 in the simulation
  * `SIC_iterations::Int64`: The maximum number of SIC iterations to perform during the decoding steps
  * `max_errored_frames::Int64`: The maximum number of frames with errors to simulate. Once a simulation reaches this number of frames with errors, the simulation will stop.
  * `overhead::Float64`: Overhead assumed for the framing and or guard bands/times in the simulation. It must be a positive number representing the overhead compared to an ideal case where all resources are fully used for sending data (e.g. no pilots, no roll-off, no guard bands, no guard times). An overhead value of `1.0` implies that the spectral efficiency is half of the ideal case.
