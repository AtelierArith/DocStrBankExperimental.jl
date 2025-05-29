```
random_magnetic_field_layer(ξ::Vector{Index{Int64}}, p::Vector{Float64})
```

Construct a layer of random Rz gates representing a random magnetic field along the z-axis.

For each qubit i, a random rotation Rz is applied with a rotation angle drawn uniformly from [0, 2 pi p*i). This gives an average rotation angle of pi p*i on each site.

# Arguments

  * `ξ::Vector{Index{Int64}}`: A vector of ITensor indices corresponding to the qubit sites.
  * `p::Vector{Float64}`: A vector of parameters (one per qubit) that set the scale of the rotation angles.

# Returns

A vector of ITensors representing the random Rz gates applied to each qubit.

# Example

```julia
circuit = random_magnetic_field_layer(siteinds("Qubit", 5), 0.1 * ones(5))
```
