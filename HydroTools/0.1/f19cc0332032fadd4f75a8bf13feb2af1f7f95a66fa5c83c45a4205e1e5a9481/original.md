```
heat_index(Tair::T, RH::T) where {T<:Real}
```

Calculate the heat index given the air temperature `Tair` (in degrees Celsius) and the relative humidity `RH` (in percent).

# Arguments

  * `Tair::T`: Air temperature in degrees Celsius.
  * `RH::T`: Relative humidity in percent.

# Returns

  * `HI::Float64`: Heat index in degrees Celsius.

# Examples

```julia-repl
julia> heat_index(30, 50)
31.049081444444305
```

# References

1. Steadman, R. G. “The Assessment of Sultriness. Part I: A Temperature-Humidity Index Based on Human Physiology and Clothing Science.” Journal of Applied Meteorology 18, no. 7 (July 1979): 861–73. https://doi.org/10.1175/1520-0450(1979)018<0861:TAOSPI>2.0.CO;2.
2. Steadman, Robert G. “A Universal Scale of Apparent Temperature.” Journal of Climate and Applied Meteorology 23, no. 12 (December 1984): 1674–87. https://doi.org/10.1175/1520-0450(1984)023<1674:AUSOAT>2.0.CO;2.
3. Rothfusz, Lans P. “The Heat Index ‘Equation’ (or, More Than You Ever Wanted to Know About Heat Index),” 1990.
4. Anderson, G. Brooke, Michelle L. Bell, and Roger D. Peng. “Methods to Calculate the Heat Index as an Exposure Metric in Environmental Health Research.” Environmental Health Perspectives 121, no. 10 (October 2013): 1111–19. https://doi.org/10.1289/ehp.1206273.
