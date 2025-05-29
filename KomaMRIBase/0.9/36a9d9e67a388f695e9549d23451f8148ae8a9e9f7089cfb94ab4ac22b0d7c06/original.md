```
seq = Sequence()
seq = Sequence(GR)
seq = Sequence(GR, RF)
seq = Sequence(GR, RF, ADC)
seq = Sequence(GR, RF, ADC, DUR)
seq = Sequence(GR::Array{Grad,1})
seq = Sequence(GR::Array{Grad,1}, RF::Array{RF,1})
seq = Sequence(GR::Array{Grad,1}, RF::Array{RF,1}, A::ADC, DUR, DEF)
```

The Sequence struct. It contains events of an MRI sequence. Most field names (except for the DEF field) consist of matrices or vectors, where each column index represents a sequence block. This struct serves as an input for the simulation.

# Arguments

  * `GR`: (`::Matrix{Grad}`) gradient matrix. Rows for x-y-z amplitudes and columns are for blocks
  * `RF`: (`::Matrix{RF}`) RF matrix. The 1 row is for the coil and columns are for blocks
  * `ADC`: (`::Array{ADC,1}`) ADC block vector
  * `DUR`: (`::Vector`, `[s]`) duration block vector
  * `DEF`: (`::Dict{String, Any}`) dictionary with relevant information of the sequence.   Possible keys could be [`"AdcRasterTime"`, `"GradientRasterTime"`, `"Name"`, `"Nz"`,   `"Num_Blocks"`, `"Nx"`, `"Ny"`, `"PulseqVersion"`, `"BlockDurationRaster"`,   `"FileName"`, `"RadiofrequencyRasterTime"`]

# Returns

  * `seq`: (`::Sequence`) Sequence struct
