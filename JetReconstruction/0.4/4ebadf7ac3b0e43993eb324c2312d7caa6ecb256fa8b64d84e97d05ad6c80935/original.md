```
ClusterSequence(algorithm::JetAlgorithm.Algorithm, p::Real, R::Float64, strategy::RecoStrategy.Strategy, jets::T, history, Qtot) where T <: FourMomentum
```

Construct a `ClusterSequence` object.

# Arguments

  * `algorithm::JetAlgorithm.Algorithm`: The algorithm used for clustering.
  * `p::Real`: The power value used for the clustering algorithm.
  * `R::Float64`: The R parameter used for the clustering algorithm.
  * `strategy::RecoStrategy.Strategy`: The strategy used for clustering.
  * `jets::Vector{T}`: The jets in the cluster sequence, which are of T <: FourMomentum
  * `history::Vector{HistoryElement}`: The branching history of the cluster sequence.
  * `Qtot::Any`: The total energy of the event.
