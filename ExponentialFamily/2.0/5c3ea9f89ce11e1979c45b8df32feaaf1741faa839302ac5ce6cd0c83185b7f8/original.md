```
ExponentialFamilyDistributionAttributes(basemeasure, sufficientstatistics, logpartition, support)
```

A structure to represent the attributes of an exponential family member.

# Fields

  * `basemeasure::B`: The basemeasure of the exponential family member.
  * `sufficientstatistics::S`: The sufficient statistics of the exponential family member.
  * `logpartition::L`: The log-partition (cumulant) of the exponential family member.
  * `support::P`: The support of the exponential family member.

# Optionally

  * `logbasemeasure::LB`: The log of the  basemeasure of the exponential family member.

See also: [`ExponentialFamilyDistribution`](@ref), [`getbasemeasure`](@ref), [`getsufficientstatistics`](@ref), [`getlogpartition`](@ref), [`getsupport`](@ref)
