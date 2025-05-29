```
scaled_rand([rng], [T], dims...;
    scaling=0.1)
```

Create and return a matrix with random values, uniformly distributed within a range defined by `scaling`.

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the matrix. Should follow `res_size x in_size`.

# Keyword arguments

  * `scaling`: A scaling factor to define the range of the uniform distribution. The matrix elements will be randomly chosen from the range `[-scaling, scaling]`. Defaults to `0.1`.

# Examples

```jldoctest
julia> res_input = scaled_rand(8, 3)
8×3 Matrix{Float32}:
 -0.0669356  -0.0292692  -0.0188943
  0.0159724   0.004071   -0.0737949
  0.026355   -0.0191563   0.0714962
 -0.0177412   0.0279123   0.0892906
 -0.0184405   0.0567368   0.0190222
  0.0944272   0.0679244   0.0148647
 -0.0799005  -0.0891089  -0.0444782
 -0.0970182   0.0934286   0.03553
```
