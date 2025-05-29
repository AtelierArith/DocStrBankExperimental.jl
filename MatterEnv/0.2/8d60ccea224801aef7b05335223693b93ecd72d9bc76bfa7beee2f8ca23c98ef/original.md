```
load_eigenval(filename::String="EIGENVAL", spin::Bool=false) -> Bands, Kpoints
```

Load band structure from EIVENVAL file.

# Arguments

  * `filename::String="EIGENVAL"`: name of input file
  * `spin::Bool=false`: distingush spin up and spin down or not

# Returns

  * `Bands`: Eigen-values of energy in each k-points
  * `Array{KPoint, 1}`: K-points and weight
