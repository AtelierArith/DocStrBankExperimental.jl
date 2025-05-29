The Monte Carlo particle - based on the lcio::MCParticle.

  * Author: F.Gaede, DESY

# Fields

  * `PDG::Int32`: PDG code of the particle
  * `generatorStatus::Int32`: status of the particle as defined by the generator
  * `simulatorStatus::Int32`: status of the particle from the simulation program - use BIT constants below
  * `charge::Float32`: particle charge
  * `time::Float32`: creation time of the particle in [ns] wrt. the event, e.g. for preassigned decays or decays in flight from the simulator.
  * `mass::Float64`: mass of the particle in [GeV]
  * `vertex::Vector3d`: production vertex of the particle in [mm].
  * `endpoint::Vector3d`: endpoint of the particle in [mm]
  * `momentum::Vector3d`: particle 3-momentum at the production vertex in [GeV]
  * `momentumAtEndpoint::Vector3d`: particle 3-momentum at the endpoint in [GeV]
  * `spin::Vector3f`: spin (helicity) vector of the particle.
  * `colorFlow::Vector2i`: color flow as defined by the generator

# Relations

  * `parents::MCParticle`: The parents of this particle.
  * `daughters::MCParticle`: The daughters this particle.

# Methods

  * `pushToParents(obj::MCParticle, robj::MCParticle)`: push related object to the `parents` relation
  * `popFromParents(obj::MCParticle)`: pop last related object from `parents` relation
  * `pushToDaughters(obj::MCParticle, robj::MCParticle)`: push related object to the `daughters` relation
  * `popFromDaughters(obj::MCParticle)`: pop last related object from `daughters` relation
