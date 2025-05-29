Simulated tracker hit

  * Author: F.Gaede, DESY

# Fields

  * `cellID::UInt64`: ID of the sensor that created this hit
  * `EDep::Float32`: energy deposited in the hit [GeV].
  * `time::Float32`: proper time of the hit in the lab frame in [ns].
  * `pathLength::Float32`: path length of the particle in the sensitive material that resulted in this hit.
  * `quality::Int32`: quality bit flag.
  * `position::Vector3d`: the hit position in [mm].
  * `momentum::Vector3f`: the 3-momentum of the particle at the hits position in [GeV]

# Relations

  * `mcparticle::MCParticle`: MCParticle that caused the hit.
