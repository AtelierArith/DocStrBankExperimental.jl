ParticleID

  * Author: F.Gaede, DESY

# Fields

  * `type::Int32`: userdefined type
  * `PDG::Int32`: PDG code of this id - ( 999999 ) if unknown.
  * `algorithmType::Int32`: type of the algorithm/module that created this hypothesis
  * `likelihood::Float32`: likelihood of this hypothesis - in a user defined normalization.
  * `parameters::PVector{Float32}`: parameters associated with this hypothesis. Check/set collection parameters ParameterNames_PIDAlgorithmTypeName for decoding the indices.

# Methods

  * `setParameters(object::ParticleID, v::AbstractVector{Float32})`: assign a set of values to the `parameters` vector member
