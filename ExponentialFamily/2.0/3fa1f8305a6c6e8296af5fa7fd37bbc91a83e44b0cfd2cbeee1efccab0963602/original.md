```
DirichletCollection{T <: Real, N, A <: AbstractArray{T, N}} <: Distribution{ArrayLikeVariate{N}, Continuous}
```

A collection of independent Dirichlet distributions, where `T` is the element type of the tensor `A`. The distribution generalizes the Dirichlet distribution to handle multiple sets of parameters organized in a tensor structure. This distribution collects multiple independent Dirichlet distributions into a single efficient interface. The Dirichlet counts for the independent Dirichlet distributions are stored along the first dimension of `a`. This distribution can be used as a conjugate prior to a Categorical distribution with mulitple switch cases (such as a discrete state-transition with controls).  

# Fields

  * `α::A`: The tensor parameter of the distribution, where each slice represents parameters of a Dirichlet distribution
  * `α0::A`: The sum of parameters along the first dimension.
  * `lmnB::A`: The log multinomial beta function values for each slice.

The distribution models multiple independent Dirichlet distributions organized in a tensor structure, where each slice `a[:,i,j,...]` represents the parameters of an independent Dirichlet distribution.
