```
modified_lm([rng], [T], dims...;
    factor, amplitude=0.3, sine_divisor=5.9, logistic_parameter=2.35,
    return_sparse=false)
```

Generate a input weight matrix based on the logistic mapping [^viehweg2025]. The matrix is built so that each input is transformed into a high-dimensional feature space via a recursive logistic map. For each input, a chain of weights is generated as follows:

  * The first element of the chain is initialized using a sine function:

$$
      W[1,j] = \text{amplitude} \cdot \sin( (j \cdot \pi) / 
          (\text{factor} \cdot \text{n} \cdot \text{sine_divisor}) )
$$

where `j` is the index corresponding to the input and `n` is the number of inputs.

  * Subsequent elements are recursively computed using the logistic mapping:

$$
      W[i+1,j] = \text{logistic_parameter} \cdot W[i,j] \cdot (1 - W[i,j])
$$

The resulting matrix has dimensions `(factor * in_size) x in_size`, where `in_size` corresponds to the number of columns provided in `dims`. If the provided number of rows does not match `factor * in_size`  the number of rows is overridden.

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the matrix. Should follow `res_size x in_size`.

# Keyword arguments

  * `factor`: The number of logistic map iterations (chain length) per input, determining the number of rows per input.
  * `amplitude`: Scaling parameter A for the sine-based initialization of the first element in each logistic chain. Default is 0.3.
  * `sine_divisor`: Parameter B used to adjust the phase in the sine initialization. Default is 5.9.
  * `logistic_parameter`: The parameter r in the logistic recurrence that governs the chain dynamics. Default is 2.35.
  * `return_sparse`: If `true`, returns the resulting matrix as a sparse matrix. Default is `false`.

# Examples

```jldoctest
julia> modified_lm(20, 10; factor=2)
20×10 SparseArrays.SparseMatrixCSC{Float32, Int64} with 18 stored entries:
⎡⢠⠀⠀⠀⠀⎤
⎢⠀⢣⠀⠀⠀⎥
⎢⠀⠀⢣⠀⠀⎥
⎢⠀⠀⠀⢣⠀⎥
⎣⠀⠀⠀⠀⢣⎦

julia> modified_lm(12, 4; factor=3)
12×4 SparseArrays.SparseMatrixCSC{Float32, Int64} with 9 stored entries:
  ⋅    ⋅          ⋅          ⋅ 
  ⋅    ⋅          ⋅          ⋅ 
  ⋅    ⋅          ⋅          ⋅ 
  ⋅   0.0133075   ⋅          ⋅ 
  ⋅   0.0308564   ⋅          ⋅ 
  ⋅   0.070275    ⋅          ⋅ 
  ⋅    ⋅         0.0265887   ⋅ 
  ⋅    ⋅         0.0608222   ⋅ 
  ⋅    ⋅         0.134239    ⋅ 
  ⋅    ⋅          ⋅         0.0398177
  ⋅    ⋅          ⋅         0.0898457
  ⋅    ⋅          ⋅         0.192168

```

[^viehweg2025]: Viehweg, Johannes, Constanze Poll, and Patrick Mäder. "Deterministic Reservoir Computing for Chaotic Time Series Prediction." arXiv preprint arXiv:2501.15615 (2025).
