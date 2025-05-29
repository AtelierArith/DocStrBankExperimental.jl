```
AddGlobalParameters(out_dim, loc; init_theta, activation)
```

Adds learnable global parameters `θ` to the input vector at indexes `loc` to  create a vector of size `out_dim`.

# Arguments:

  * `out_dim::Int`: Length of the resulting output vector.
  * `loc::Int`: Indexes of θ in the output vector.
  * `init_theta`: Initialization function for `θ` from WeightInitializers.jl. Default = glorot_uniform.
  * `activation`: Activation function to use on `θ`. Default = softplus.

# Examples

```jldoctest
julia> layer = AddGlobalParameters(4, [2, 4])
AddGlobalParameters()  # 2 parameters, plus 16 non-trainable
 
julia> layer([1; 2;;], ps, st)[1] # returns y, st
4×1 Matrix{Float32}:
 1.0
 θ₁
 2.0
 θ₂
```
