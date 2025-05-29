Reconstructed Particle

  * Author: F.Gaede, DESY

# Fields

  * `type::Int32`: type of reconstructed particle. Check/set collection parameters ReconstructedParticleTypeNames and ReconstructedParticleTypeValues.
  * `energy::Float32`: [GeV] energy of the reconstructed particle. Four momentum state is not kept consistent internally.
  * `momentum::Vector3f`: [GeV] particle momentum. Four momentum state is not kept consistent internally.
  * `referencePoint::Vector3f`: [mm] reference, i.e. where the particle has been measured
  * `charge::Float32`: charge of the reconstructed particle.
  * `mass::Float32`: [GeV] mass of the reconstructed particle, set independently from four vector. Four momentum state is not kept consistent internally.
  * `goodnessOfPID::Float32`: overall goodness of the PID on a scale of [0;1]
  * `covMatrix::SVector{10,Float32}`: cvariance matrix of the reconstructed particle 4vector (10 parameters). Stored as lower triangle matrix of the four momentum (px,py,pz,E), i.e. cov(px,px), cov(py,##

# Relations

  * `startVertex::Vertex`: start vertex associated to this particle
  * `particleIDUsed::ParticleID`: particle Id used for the kinematics of this particle
  * `clusters::Cluster`: clusters that have been used for this particle.
  * `tracks::Track`: tracks that have been used for this particle.
  * `particles::ReconstructedParticle`: reconstructed particles that have been combined to this particle.
  * `particleIDs::ParticleID`: particle Ids (not sorted by their likelihood)

# Methods

  * `pushToClusters(obj::ReconstructedParticle, robj::Cluster)`: push related object to the `clusters` relation
  * `popFromClusters(obj::ReconstructedParticle)`: pop last related object from `clusters` relation
  * `pushToTracks(obj::ReconstructedParticle, robj::Track)`: push related object to the `tracks` relation
  * `popFromTracks(obj::ReconstructedParticle)`: pop last related object from `tracks` relation
  * `pushToParticles(obj::ReconstructedParticle, robj::ReconstructedParticle)`: push related object to the `particles` relation
  * `popFromParticles(obj::ReconstructedParticle)`: pop last related object from `particles` relation
  * `pushToParticleIDs(obj::ReconstructedParticle, robj::ParticleID)`: push related object to the `particleIDs` relation
  * `popFromParticleIDs(obj::ReconstructedParticle)`: pop last related object from `particleIDs` relation
