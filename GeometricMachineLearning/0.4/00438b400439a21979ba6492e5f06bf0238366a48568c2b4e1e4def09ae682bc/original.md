```
Batch
```

`Batch` is a struct whose functor acts on an instance of `DataLoader` to produce a sequence of training samples for training for one epoch. 

See [`Batch(::Int)`](@ref) and [`Batch(::Int, ::Int, ::Int)`](@ref) for the different constructors.

# The functor

An instance of `Batch` can be called on an instance of `DataLoader` to produce a sequence of samples that contain all the input data, i.e. for training for one epoch. 

The output of applying `batch:Batch` to `dl::DataLoader` is a tuple of vectors of integers. Each of these vectors contains two integers: the first is the *time index* and the second one is the *parameter index*.

# Examples

Consider the following example for drawing batches of size 2 for an instance of `DataLoader` constructed with a vector:

```jldoctest
using GeometricMachineLearning
import Random

rng = Random.TaskLocalRNG()
Random.seed!(rng, 123)

dl = DataLoader(rand(rng, 5))
batch = Batch(2)

batch(dl)

# output

[ Info: You have provided a matrix as input. The axes will be interpreted as (i) system dimension and (ii) number of parameters.
([(1, 5), (1, 3)], [(1, 4), (1, 1)], [(1, 2)])
```

Here the first index is always 1 (the time dimension). We get a total number of 3 batches.  The last batch is only of size 1 because we *sample without replacement*. Also see the docstring for [`DataLoader(::AbstractVector)`](@ref).
