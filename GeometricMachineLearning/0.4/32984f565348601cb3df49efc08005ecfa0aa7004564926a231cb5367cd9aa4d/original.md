```
DataLoader(data::AbstractVector)
```

Make an instance of `DataLoader` based on a vector.

# Extended help

If the input to `DataLoader` is a vector, it is assumed that this vector represents one-dimensional time-series data and is therefore processed as:

```julia
    DataLoader(data::AbstractVector; autoencoder=true) = DataLoader(reshape(data, 1, length(data)); autoencoder = autoencoder)
```
