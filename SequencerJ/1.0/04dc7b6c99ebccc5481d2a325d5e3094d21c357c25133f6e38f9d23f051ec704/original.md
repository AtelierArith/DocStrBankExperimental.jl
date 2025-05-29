```
sequence(A::VecOrMat{T}; 
    scales=nothing,
    metrics=ALL_METRICS,
    grid=nothing,
    ) where {T <: Real}
```

Analyze the provided `m x n` matrix (or m vectors of vectors n) by applying one or more 1-dimensional statistical metrics to  each column of data, possibly after dividing the data into smaller row sets. Columns are compared pairwise for each combination  of metric and scale to create a n x n distance matrix that is analyzed as a graph using a novel algorithm. Details of the algorithm are provided in the paper cited below, by D. Baron and B. Ménard.

```julia
sequence(A, metrics=ALL_METRICS, scales=nothing)
```

or equivalently:

```julia
sequence(A)
```

as `metrics=ALL_METRICS` and `scales=nothing` are defaults. If you want to specify only one metric, you must wrap it in a 1-tuple. e.g. to use only KL Divergence, write:

```julia
sequence(A, metrics=(KLD,), scales=nothing
```

Use the `scales` keyword to specify the number of "chunks" into which the data should be divided, as a tuple, e.g. 

```julia
sequence(A, scales=(1,3,5))
```

In the `autoscale` mode (enabled by default as `scales=nothing`) SequencerJ will find its own "best scale" based on  running the Sequencer against a sample of columns (10% for now) and picking the scale that results in the greatest elongation.

A 1-D grid may be provided. The grid - whose deltas figure in the distance calculations - must be non-negative  real numbers (Float16, Float32, or Float64). The grid length must equal the number of rows in A.

```julia
julia> sequence(A; metrics=(WASS1D,L2), grid=collect(0.5:0.5:size(A,1))) # grid must equal the size of A along dim 1
```

The paper that describes the Sequencer algorithm and its applications can be found  on [Arxiv](https://arxiv.org/abs/2006.13948).
