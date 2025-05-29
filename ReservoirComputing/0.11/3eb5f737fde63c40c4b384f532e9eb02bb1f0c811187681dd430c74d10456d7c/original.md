```
logistic_mapping([rng], [T], dims...;
    amplitude=0.3, sine_divisor=5.9, logistic_parameter=3.7,
    return_sparse=false)
```

Generate an input weight matrix using a logistic mapping [^wang2022].The first row is initialized using a sine function:

$$
    W[1, j] = \text{amplitude} \cdot \sin(j \cdot \pi / 
        (\text{sine_divisor} \cdot in_size))
$$

for each input index `j`, with `in_size` being the number of columns provided in `dims`. Subsequent rows are generated recursively using the logistic map recurrence:

$$
    W[i+1, j] = \text{logistic_parameter} \cdot W(i, j) \cdot (1 - W[i, j])
$$

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the matrix. Should follow `res_size x in_size`.

# Keyword arguments

  * `amplitude`: Scaling parameter used in the sine initialization of the first row. Default is 0.3.
  * `sine_divisor`: Parameter used to adjust the phase in the sine initialization. Default is 5.9.
  * `logistic_parameter`: The parameter in the logistic mapping recurrence that governs the dynamics. Default is 3.7.
  * `return_sparse`: If `true`, returns the resulting matrix as a sparse matrix. Default is `false`.

# Examples

```jldoctest
julia> logistic_mapping(8, 3)
8×3 Matrix{Float32}:
 0.0529682  0.104272  0.1523
 0.185602   0.345578  0.477687
 0.559268   0.836769  0.923158
 0.912003   0.50537   0.262468
 0.296938   0.924893  0.716241
 0.772434   0.257023  0.751987
 0.650385   0.70656   0.69006
 0.841322   0.767132  0.791346

```

[^wang2022]: Wang, Heshan, et al. "Echo state network with logistic mapping and bias dropout for time series prediction." Neurocomputing 489 (2022): 196-210.
