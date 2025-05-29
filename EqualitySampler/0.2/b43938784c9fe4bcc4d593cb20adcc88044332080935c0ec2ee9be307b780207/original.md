```
CustomInclusionPartitionDistribution(k::T, logpdf::NTuple{N, Float64})
```

CustomInclusionPartitionDistribution is similar to the BetaBinomialPartitionDistribution in that the model probabilities are completely determined by the size of the partition. Whereas the BetaBinomialPartitionDistribution uses a BetaBinomial distribution to obtain the probabilities, the CustomInclusionPartitionDistribution can be used to specify any vector of probabilities. This distribution is particularly useful to sample uniformly from partitions of a given size. For example:

```julia
rand(CustomInclusionPartitionDistribution(4, ntuple(i->log(i==1), Val(4)))) # always all equal (1 parameter)
rand(CustomInclusionPartitionDistribution(4, ntuple(i->log(i==3), Val(4)))) # always 3 parameters
rand(CustomInclusionPartitionDistribution(4, ntuple(i->log(i==4), Val(4)))) # always completely distinct (4 parameters)
```

The function does not check if sum(exp, logpdf) ≈ 1.0, that is the callers responsibility.
