```
ee_genkt_algorithm(particles::AbstractVector{T}; p = -1, R = 4.0,
                   algorithm::JetAlgorithm.Algorithm = JetAlgorithm.Durham,
                   recombine = +) where {T}
```

Run an e+e- reconstruction algorithm on a set of initial particles.

# Arguments

  * `particles::AbstractVector{T}`: A vector of particles to be clustered.
  * `p = 1`: The power parameter for the algorithm. Not required / ignored for the Durham algorithm when it is set to 1.
  * `R = 4.0`: The jet radius parameter. Not required / ignored for the Durham algorithm.
  * `algorithm::JetAlgorithm.Algorithm = JetAlgorithm.Durham`: The specific jet algorithm to use.
  * `recombine`: The recombination scheme to use. Defaults to `+`.

# Returns

  * The result of the jet clustering as a `ClusterSequence` object.

# Notes

This is the public interface to the e+e- jet clustering algorithm. The function will check for consistency between the algorithm and the power parameter as needed. It will then prepare the internal EDM particles for the clustering itself, and call the actual reconstruction method `_ee_genkt_algorithm`.

If the algorithm is Durham, `p` is set to 1 and `R` is nominally set to 4.

Note that unlike `pp` reconstruction the algorithm has to be specified explicitly.
