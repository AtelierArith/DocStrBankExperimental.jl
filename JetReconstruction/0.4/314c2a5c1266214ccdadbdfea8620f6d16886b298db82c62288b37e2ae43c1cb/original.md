```
struct ClusterSequence
```

A struct holding the full history of a jet clustering sequence, including the final jets.

# Fields

  * `algorithm::JetAlgorithm.Algorithm`: The algorithm used for clustering.
  * `strategy::RecoStrategy.Strategy`: The strategy used for clustering.
  * `power::Float64`: The power value used for the clustering algorithm (not that this value is always stored as a Float64 to be type stable)
  * `R::Float64`: The R parameter used for the clustering algorithm.
  * `jets::Vector{T}`: The actual jets in the cluster sequence, which are of type `T <: FourMomentum`.
  * `n_initial_jets::Int`: The initial number of particles used for exclusive jets.
  * `history::Vector{HistoryElement}`: The branching history of the cluster sequence. Each stage in the history indicates where to look in the jets vector to get the physical PseudoJet.
  * `Qtot::Any`: The total energy of the event.
