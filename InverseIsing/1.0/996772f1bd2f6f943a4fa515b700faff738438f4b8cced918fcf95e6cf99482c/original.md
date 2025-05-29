```
fit(gbm::GBM, X::AbstractArray; delta=1e-1 [, opts])
```

Fit the weight parameters of GBM to data `X`.

# Arguments

  * `delta::Float`: Threshold for thinning out parameters.

Options that can be provided in the `opts` dictionary:

  * `:alpha` - Decay rate of the L1 regularization term. (default: 0.01)
  * `:beta` - Inverse temperature. (default: 1.0)
  * `:lr` - Learning rate. (default: 1.0)
  * `:epochs` - Maximum permissible number of step in SGD. (default: 20)
  * `:n_iter` - Number of learning repetitions. (default: 100)

# References

  * E. Aurell & M. Ekeberg, Phys. Rev. Lett. **108**, 090201 (2012).

# Examples

```jldoctest
julia> using InverseIsing

julia> samples = [1 -1 -1;] # Spin configuration.

julia> model = GBM(3) # Set the number of units.

julia> fit(model, samples)

julia> W = infer(model); output = decode(W)

julia> output
OrderedCollections.OrderedDict{Tuple{Int64,Int64},Int64} with 3 entries:
  (1, 2) => -1
  (1, 3) => -1
  (2, 3) => 1
```

```
The above example means that the interaction between (1, 2) and (1, 3) is
antiferromagnetic bond and only (2, 3) is ferromagnetic bond.
```
