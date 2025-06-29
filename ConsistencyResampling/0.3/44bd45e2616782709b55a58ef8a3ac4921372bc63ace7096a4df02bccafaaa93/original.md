```
Consistent(predictions::AbstractVector)
```

Create an object that can be used for resampling `predictions` and corresponding targets.

The set of predictions has to be provided as a vector consisting of

  * probabilities,
  * vectors of probabilities summing up to 1,
  * or distributions that can be sampled from.

Consistency resampling can be performed with `rand` and `rand!`, as described in the documentation of [`Random`](https://docs.julialang.org/en/v1/stdlib/Random/).

# Examples

```jldoctest
julia> predictions = rand(100);

julia> consistent = Consistent(predictions);

julia> rand(consistent) isa Tuple{Float64,Bool}
true

julia> first(rand(consistent)) in predictions
true
```

!!! note
    One can use `Random.Sampler` to create a sampler that is optimized for the generation of multiple samples, e.g., by building an alias table:

    ```jldoctest
    julia> using Random: Sampler, GLOBAL_RNG

    julia> sampler = Sampler(GLOBAL_RNG, Consistent(rand(100)));

    julia> rand(sampler) isa Tuple{Float64,Bool}
    true
    ```

    However, for small number of samples the setup cost can outweigh the improved sampling efficiency.


!!! note
    Multiple samples are returned as an array of tuples of predictions and corresponding targets. If you prefer a tuple of arrays of predictions and targets instead, you can use a package such as [StructArrays](https://github.com/JuliaArrays/StructArrays.jl) and perform in-place sampling:

    ```jldoctest
    julia> using StructArrays, Random

    julia> predictions = Vector{Float64}(undef, 100);

    julia> targets = Vector{Bool}(undef, 100);

    julia> rand!(StructVector((predictions, targets)), Consistent(rand(100)));
    ```


# References

Bröcker, J. and Smith, L.A., 2007. [Increasing the reliability of reliability diagrams](https://doi.org/10.1175/WAF993.1). Weather and forecasting, 22(3), pp. 651-661.
