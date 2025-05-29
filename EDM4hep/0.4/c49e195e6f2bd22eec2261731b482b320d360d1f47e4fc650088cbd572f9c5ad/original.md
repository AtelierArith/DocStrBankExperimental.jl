Simulated calorimeter hit

  * Author: F.Gaede, DESY

# Fields

  * `cellID::UInt64`: ID of the sensor that created this hit
  * `energy::Float32`: energy of the hit in [GeV].
  * `position::Vector3f`: position of the hit in world coordinates in [mm].

# Relations

  * `contributions::CaloHitContribution`: Monte Carlo step contribution - parallel to particle

# Methods

  * `pushToContributions(obj::SimCalorimeterHit, robj::CaloHitContribution)`: push related object to the `contributions` relation
  * `popFromContributions(obj::SimCalorimeterHit)`: pop last related object from `contributions` relation
