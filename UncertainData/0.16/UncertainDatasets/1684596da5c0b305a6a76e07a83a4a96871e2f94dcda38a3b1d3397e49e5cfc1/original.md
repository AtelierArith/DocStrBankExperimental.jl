```
UncertainIndexValueDataset{
    IDXTYP<:AbstractUncertainIndexDataset, 
    VALSTYP<:AbstractUncertainValueDataset}
```

A generic dataset type consisting of a set of uncertain `indices` (e.g. time, depth, order, etc...) and a set of uncertain `values`. 

The i-th index is assumed to correspond to the i-th value. For example, if  `data` is an instance of a `UncertainIndexValueDataset`, then 

  * `data.indices[2]` is the index for the value `data.values[2]`
  * `data.values[7]` is the value for the index `data.indices[7]`.
  * `data[3]` is an index-value tuple `(data.indices[3], data.values[3])`.

## Fields

  * **`indices::T where {T <: AbstractUncertainIndexDataset}`**: The uncertain indices,   represented by some type of uncertain index dataset.
  * **`values::T  where {T <: AbstractUncertainValueDataset}`**: The uncertain values,   represented by some type of uncertain index dataset.

## Example

```julia
# Simulate some data values measured a specific times.
times = 1:100
values = sin.(0.0:0.1:100.0)

# Assume the data were measured by a device with normally distributed
# measurement uncertainties with fluctuating standard deviations
σ_range = (0.1, 0.7)

uncertain_values = [UncertainValue(Normal, val, rand(Uniform(σ_range...))) 
    for val in values]

# Assume the clock used to record the times is uncertain, but with uniformly 
# distributed noise that doesn't change through time.
uncertain_times = [UncertainValue(Uniform, t-0.1, t+0.1) for t in times]

# Pair the time-value data. If vectors are provided to the constructor,
# the first will be interpreted as the indices and the second as the values.
data = UncertainIndexValueDataset(uncertain_times, uncertain_values)

# A safer option is to first convert to UncertainIndexDataset and 
# UncertainValueDataset, so you don't accidentally mix the indices 
# and the values.
uidxs = UncertainIndexDataset(uncertain_times)
uvals = UncertainValueDataset(uncertain_values)

data = UncertainIndexValueDataset(uidxs, uvals)
```
