```
ngwp_analysis(G::GraphSig, wavelet_packet::Array{Float64,3})
```

For a GraphSig object `G`, generate the matrix of NGWP expansion coefficients.

# Input Arguments

  * `G::GraphSig`: an input GraphSig object
  * `wavelet_packet::Array{Float64,3}`: the varimax wavelets packet.

# Output Argument

  * `dmatrix::Array{Float64,3}`: the expansion coefficients matrix.
