Monte Carlo contribution to SimCalorimeterHit

  * Author: F.Gaede, DESY

# Fields

  * `PDG::Int32`: PDG code of the shower particle that caused this contribution.
  * `energy::Float32`: energy in [GeV] of the this contribution
  * `time::Float32`: time in [ns] of this contribution
  * `stepPosition::Vector3f`: position of this energy deposition (step) [mm]

# Relations

  * `particle::MCParticle`: primary MCParticle that caused the shower responsible for this contribution to the hit.
