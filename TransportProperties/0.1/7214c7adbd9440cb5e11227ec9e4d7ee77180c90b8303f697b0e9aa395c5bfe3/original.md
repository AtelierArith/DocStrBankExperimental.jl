Function to calculate self diffusion coefficients

# Usage

```
D_ii!(D::Array{Float64},sp_trd::Array{TransportData}, T::Float64, p::Float64, molwt::Array{Float64})
```

  * D : Array to store the diffusion coefficients (size N)
  * sp_trd : Array of species transport data
  * T : Temperature (K)
  * p : Pressure (Pa
  * molwt : specoes molecular weights
