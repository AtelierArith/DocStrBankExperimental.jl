```
block_distribution(x_input::AbstractVector; block_size::Integer) = 
    block_distribution(mean, x_input, block_size::Integer)
block_distribution(by::Function, x_input::AbstractVector, block_size::Integer)
```

Given the data and the block size, computes the distribution of estimates of the  properties for each block. Returns a `BlockDistribution{NBLOCKS}` object. The block size must be an integer.

# Example

```julia-repl
julia> using MolSimToolkit

julia> x = BlockAverages.test_data(10^7);

julia> d = block_distribution(x; block_size = 25*10^3)
-------------------------------------------------------------------
BlockDistribution{400}
-------------------------------------------------------------------
Number of blocks: 400
Estimated value: = 0.025151622077551537
Standard error of the mean: 0.05596145099711976
Standard deviation of the mean: 1.119229019942395
> block_mean contains the mean computed for each block.
-------------------------------------------------------------------
```

The distribution is stored in the `d.block_mean` vector, and can be plotted with:

```julia-repl
julia> using Plots

julia> histogram(d)
```
