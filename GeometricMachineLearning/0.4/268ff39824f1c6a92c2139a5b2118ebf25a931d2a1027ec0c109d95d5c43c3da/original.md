```
DataLoader(data)
```

Make an instance based on a data set.

This is designed to make training convenient.

# Fields of `DataLoader`

The fields of the `DataLoader` struct are the following: 

  * `input`: The input data with axes (i) system dimension, (ii) number of time steps and (iii) number of parameters.
  * `output`: The tensor that contains the output (supervised learning) - this may be of type `Nothing` if the constructor is only called with one tensor (unsupervised learning).
  * `input_dim`: The *dimension* of the system, i.e. what is taken as input by a regular neural network.
  * `input_time_steps`: The length of the entire time series (length of the second axis).
  * `n_params`: The number of parameters that are present in the data set (length of third axis)
  * `output_dim`: The dimension of the output tensor (first axis). If `output` is of type `Nothing`, then this is also of type `Nothing`.
  * `output_time_steps`: The size of the second axis of the output tensor. If `output` is of type `Nothing`, then this is also of type `Nothing`.

# Implementation

Even though `DataLoader` can be called with inputs of various forms, internally it always stores tensors with three axes.

```jldoctest
using GeometricMachineLearning

data = [1 2 3; 4 5 6]
dl = DataLoader(data)
dl.input

# output

[ Info: You have provided a matrix as input. The axes will be interpreted as (i) system dimension and (ii) number of parameters.
2×1×3 Array{Int64, 3}:
[:, :, 1] =
 1
 4

[:, :, 2] =
 2
 5

[:, :, 3] =
 3
 6
```
