Calorimeter hit

  * Author: F.Gaede, DESY

# Fields

  * `cellID::UInt64`: detector specific (geometrical) cell id.
  * `energy::Float32`: energy of the hit in [GeV].
  * `energyError::Float32`: error of the hit energy in [GeV].
  * `time::Float32`: time of the hit in [ns].
  * `position::Vector3f`: position of the hit in world coordinates in [mm].
  * `type::Int32`: type of hit. Mapping of integer types to names via collection parameters "CalorimeterHitTypeNames" and "CalorimeterHitTypeValues".
