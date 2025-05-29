```
DataLoader(data::AbstractArray{<:Number, 3})
```

Make an instance of DataLoader for data that are in tensor format.

# Arguments

There are two optional keyword arguments:

  * `autoencoder = false` and
  * `suppress_info = false`.

By default the data are stored as `TimeSeries` type. If you want to train an [`AutoEncoder`](@ref) with your data call:

```julia
    DataLoader(data; autoencoder = true)
```

The default is equivalent to `autoencoder = false`.

By default we have:

```jldoctest
using GeometricMachineLearning

data = [ 1;  2;  3;; 
         4;  5;  6;;;
         7;  8;  9;; 
        10; 11; 12]

DataLoader(data)

# output

┌ Info: You have provided a tensor with three axes as input. They will be interpreted as
└  (i) system dimension, (ii) number of time steps and (iii) number of params.
DataLoader{Int64, Array{Int64, 3}, Nothing, :TimeSeries}([1 4; 2 5; 3 6;;; 7 10; 8 11; 9 12], nothing, 3, 2, 2, nothing, nothing)
```

But if we write

```jldoctest
using GeometricMachineLearning

data = [ 1;  2;  3;; 
         4;  5;  6;;;
         7;  8;  9;; 
        10; 11; 12]

DataLoader(data; suppress_info = true)

# output

DataLoader{Int64, Array{Int64, 3}, Nothing, :TimeSeries}([1 4; 2 5; 3 6;;; 7 10; 8 11; 9 12], nothing, 3, 2, 2, nothing, nothing)
```

the `@info` statement is not printed.
