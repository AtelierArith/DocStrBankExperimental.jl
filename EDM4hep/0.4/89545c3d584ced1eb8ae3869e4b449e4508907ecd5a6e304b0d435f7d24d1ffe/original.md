Vertex

  * Author: F.Gaede, DESY

# Fields

  * `primary::Int32`: boolean flag, if vertex is the primary vertex of the event
  * `chi2::Float32`: chi-squared of the vertex fit
  * `probability::Float32`: probability of the vertex fit
  * `position::Vector3f`: [mm] position of the vertex.
  * `covMatrix::SVector{6,Float32}`: covariance matrix of the position (stored as lower triangle matrix, i.e. cov(xx),cov(y,x),cov(z,x),cov(y,y),... )
  * `algorithmType::Int32`: type code for the algorithm that has been used to create the vertex - check/set the collection parameters AlgorithmName and AlgorithmType.
  * `parameters::PVector{Float32}`: additional parameters related to this vertex - check/set the collection parameter "VertexParameterNames" for the parameters meaning.

# Relations

  * `associatedParticle::POD`: reconstructed particle associated to this vertex.

# Methods

  * `setParameters(object::Vertex, v::AbstractVector{Float32})`: assign a set of values to the `parameters` vector member
