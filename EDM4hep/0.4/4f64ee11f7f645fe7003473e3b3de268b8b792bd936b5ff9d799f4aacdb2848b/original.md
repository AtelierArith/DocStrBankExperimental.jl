dN/dx or dE/dx info of Track.

  * Author: Wenxing Fang, IHEP

# Fields

  * `dQdx::Quantity`: the reconstructed dEdx or dNdx and its error
  * `particleType::Int16`: particle type, e(0),mu(1),pi(2),K(3),p(4).
  * `type::Int16`: type.
  * `hypotheses::SVector{5,Hypothesis}`: 5 particle hypothesis
  * `hitData::PVector{HitLevelData}`: hit level data

# Relations

  * `track::Track`: the corresponding track.

# Methods

  * `setHitData(object::RecDqdx, v::AbstractVector{HitLevelData})`: assign a set of values to the `hitData` vector member
