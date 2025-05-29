Simulated Primary Ionization

  * Author: Wenxing Fang, IHEP

# Fields

  * `cellID::UInt64`: cell id.
  * `time::Float32`: the primary ionization's time in the lab frame [ns].
  * `position::Vector3d`: the primary ionization's position [mm].
  * `type::Int16`: type.
  * `electronCellID::PVector{UInt64}`: cell id.
  * `electronTime::PVector{Float32}`: the time in the lab frame [ns].
  * `electronPosition::PVector{Vector3d}`: the position in the lab frame [mm].
  * `pulseTime::PVector{Float32}`: the pulse's time in the lab frame [ns].
  * `pulseAmplitude::PVector{Float32}`: the pulse's amplitude [fC].

# Relations

  * `mcparticle::MCParticle`: the particle that caused the ionizing collisions.

# Methods

  * `setElectronCellID(object::SimPrimaryIonizationCluster, v::AbstractVector{UInt64})`: assign a set of values to the `electronCellID` vector member
  * `setElectronTime(object::SimPrimaryIonizationCluster, v::AbstractVector{Float32})`: assign a set of values to the `electronTime` vector member
  * `setElectronPosition(object::SimPrimaryIonizationCluster, v::AbstractVector{Vector3d})`: assign a set of values to the `electronPosition` vector member
  * `setPulseTime(object::SimPrimaryIonizationCluster, v::AbstractVector{Float32})`: assign a set of values to the `pulseTime` vector member
  * `setPulseAmplitude(object::SimPrimaryIonizationCluster, v::AbstractVector{Float32})`: assign a set of values to the `pulseAmplitude` vector member
