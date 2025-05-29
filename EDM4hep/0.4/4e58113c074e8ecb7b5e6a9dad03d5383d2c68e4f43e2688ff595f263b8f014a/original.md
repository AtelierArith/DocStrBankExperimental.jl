Calorimeter Hit Cluster

  * Author: F.Gaede, DESY

# Fields

  * `type::Int32`: flagword that defines the type of cluster. Bits 16-31 are used internally.
  * `energy::Float32`: energy of the cluster [GeV]
  * `energyError::Float32`: error on the energy
  * `position::Vector3f`: position of the cluster [mm]
  * `positionError::SVector{6,Float32}`: covariance matrix of the position (6 Parameters)
  * `iTheta::Float32`: intrinsic direction of cluster at position  Theta. Not to be confused with direction cluster is seen from IP.
  * `phi::Float32`: intrinsic direction of cluster at position - Phi. Not to be confused with direction cluster is seen from IP.
  * `directionError::Vector3f`: covariance matrix of the direction (3 Parameters) [mm^2]
  * `shapeParameters::PVector{Float32}`: shape parameters - check/set collection parameter ClusterShapeParameters for size and names of parameters.
  * `subdetectorEnergies::PVector{Float32}`: energy observed in a particular subdetector. Check/set collection parameter ClusterSubdetectorNames for decoding the indices of the array.

# Relations

  * `clusters::Cluster`: clusters that have been combined to this cluster.
  * `hits::CalorimeterHit`: hits that have been combined to this cluster.
  * `particleIDs::ParticleID`: particle IDs (sorted by their likelihood)

# Methods

  * `setShapeParameters(object::Cluster, v::AbstractVector{Float32})`: assign a set of values to the `shapeParameters` vector member
  * `setSubdetectorEnergies(object::Cluster, v::AbstractVector{Float32})`: assign a set of values to the `subdetectorEnergies` vector member
  * `pushToClusters(obj::Cluster, robj::Cluster)`: push related object to the `clusters` relation
  * `popFromClusters(obj::Cluster)`: pop last related object from `clusters` relation
  * `pushToHits(obj::Cluster, robj::CalorimeterHit)`: push related object to the `hits` relation
  * `popFromHits(obj::Cluster)`: pop last related object from `hits` relation
  * `pushToParticleIDs(obj::Cluster, robj::ParticleID)`: push related object to the `particleIDs` relation
  * `popFromParticleIDs(obj::Cluster)`: pop last related object from `particleIDs` relation
