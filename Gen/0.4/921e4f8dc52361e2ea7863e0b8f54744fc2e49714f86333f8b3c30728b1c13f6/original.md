```
HomogeneousMixture(distribution::Distribution, dims::Vector{Int})
```

Define a new distribution that is a mixture of some number of instances of single base distributions.

The first argument defines the base distribution of each component in the mixture.

The second argument must have length equal to the number of arguments taken by the base distribution.  A value of 0 at a position in the vector an indicates that the corresponding argument to the base distribution is a scalar, and integer values of i for i >= 1 indicate that the corresponding argument is an i-dimensional array.

Example:

```julia
mixture_of_normals = HomogeneousMixture(normal, [0, 0])
```

The resulting distribution (e.g. `mixture_of_normals` above) can then be used like the built-in distribution values like `normal`. The distribution takes `n+1` arguments where `n` is the number of arguments taken by the base distribution. The first argument to the distribution is a vector of non-negative mixture weights, which must sum to 1.0. The remaining arguments to the distribution correspond to the arguments of the base distribution, but have a different type: If an argument to the base distribution is a scalar of type `T`, then the corresponding argument to the mixture distribution is a `Vector{T}`, where each element of this vector is the argument to the corresponding mixture component. If an argument to the base distribution is an `Array{T,N}` for some `N`, then the corresponding argument to the mixture distribution is of the form `arr::Array{T,N+1}`, where each slice of the array of the form `arr[:,:,...,i]` is the argument for the `i`th mixture component.

Example:

```julia
mixture_of_normals = HomogeneousMixture(normal, [0, 0])
mixture_of_mvnormals = HomogeneousMixture(mvnormal, [1, 2])

@gen function foo()
    # mixture of two normal distributions
    # with means -1.0 and 1.0
    # and standard deviations 0.1 and 10.0
    # the first normal distribution has weight 0.4; the second has weight 0.6
    x ~ mixture_of_normals([0.4, 0.6], [-1.0, 1.0], [0.1, 10.0])

    # mixture of two multivariate normal distributions
    # with means: [0.0, 0.0] and [1.0, 1.0]
    # and covariance matrices: [1.0 0.0; 0.0 1.0] and [10.0 0.0; 0.0 10.0]
    # the first multivariate normal distribution has weight 0.4;
    # the second has weight 0.6
    means = [0.0 1.0; 0.0 1.0] # or, cat([0.0, 0.0], [1.0, 1.0], dims=2)
    covs = cat([1.0 0.0; 0.0 1.0], [10.0 0.0; 0.0 10.0], dims=3)
    y ~ mixture_of_mvnormals([0.4, 0.6], means, covs)
end
```
