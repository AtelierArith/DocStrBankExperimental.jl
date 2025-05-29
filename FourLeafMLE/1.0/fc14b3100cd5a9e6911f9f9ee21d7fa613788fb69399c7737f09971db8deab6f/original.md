```
fourLeafMLE(SITE_PATTERN_DATA)
```

# Description

Attempt to return a unique global maximum by computing the local maxima over the interior of the model as well as all submodels, and returning a list of only those which maximize the likelihood.

# Arguments

  * `SITE_PATTERN_DATA` : A site frequency vector of length 8, specifying the number of times each site                       pattern is observed in the data. The patterns are ordered as `[xxxx, xxxy, xxyx,                       xxyy, xyxx, xyxy, xyyx, xyyy]` where x and y signify different nucleotides. For                       example, the vector `SITE_PATTERN_DATA=[14,2,5,10,7,4,3,6]` means that pattern                       xxxx is observed 14 times, pattern xxxy is observed 2 times, pattern xxyx is                       observe 5 times, and so forth.

# Output

A list of vectors corresponding to trees (or submodels) which maximize the likelihood. Each vector corresponds to a located maximum and takes the form

```

[logL,
 reduced tree class,
 list of compatible binary quartet topologies,
 branch lengths (excluding those which equal 0 or 1),
 branch length names,
 labels,
 verbal description]

```

Here, the 'reduced tree class' refers to a scheme developed by the authors to categorize submodels by the type of computations required to find their local maxima. There are 10 nontrivial classes (i.e., which having nonzero likelihoods for generic data), denoted R1, R2, ..., R10. For example, R1 = binary quartet, R2 = star tree, and R3 through R10 refer to additional submodel types whose details can be found in the comments of the file `aux-functions-for-R3-through-R10.jl`.

If two or more local maxima are found which maximize the likelihood, then this function will return more than one maximum likelihood estimator. There are two possible reasons for this (1) the MLE is indeed not unique, or (2) the floating point arithmetic is insufficiently precise to distinguish which maxima has greater likelihood.

# Example usage:

```

random_hadamard_edge_parameters=rand(5)
test_model=computeProbabilityVector(random_hadamard_edge_parameters,1)
N=1000
SITE_PATTERN_DATA = rand(Multinomial(N,test_model))
fourLeafMLE(SITE_PATTERN_DATA)
listMaxima(SITE_PATTERN_DATA)

```
