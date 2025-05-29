Reconstructed Ionization Cluster

  * Author: Wenxing Fang, IHEP

# Fields

  * `cellID::UInt64`: cell id.
  * `significance::Float32`: significance.
  * `type::Int16`: type.

# Relations

  * `trackerPulse::TrackerPulse`: the TrackerPulse used to create the ionization cluster.

# Methods

  * `pushToTrackerPulse(obj::RecIonizationCluster, robj::TrackerPulse)`: push related object to the `trackerPulse` relation
  * `popFromTrackerPulse(obj::RecIonizationCluster)`: pop last related object from `trackerPulse` relation
