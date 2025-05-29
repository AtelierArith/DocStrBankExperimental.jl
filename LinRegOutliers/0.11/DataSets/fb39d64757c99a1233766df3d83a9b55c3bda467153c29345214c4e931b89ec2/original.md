Scottish Hill Races Data

# Components

  * `dist::AbstractVector{Float64}`: Distance in miles (Independent).
  * `climb::AbstractVector{Float64}`: Heights in feet (Independent).
  * `time::AbstractVector{Float64}`: Record times in hours (Dependent).

# Model

time ~ dist + climb

# References

A.C. Atkinson (1986) Comment: Aspects of diagnostic regression analysis. Statistical Science 1, 397-402.
