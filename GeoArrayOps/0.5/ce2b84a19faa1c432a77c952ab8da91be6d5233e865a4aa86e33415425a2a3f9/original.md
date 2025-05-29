```
B, flags = pmf(A; ωₘ, slope, dhₘ, dh₀, cellsize, adjust, erode)
```

Applies the progressive morphological filter by *Zhang et al. (2003)* [^zhang2003] to `A`.

# Output

  * `B::Array{T,2}` Maximum allowable values
  * `flags::Array{Float64,2}` A sized array with window sizes if filtered, zero if not filtered.

Afterwards, one can retrieve the resulting mask for `A` by `A .<= B` or `flags .== 0.`.

# Arguments

  * `A::Array{T,2}` Input Array
  * `ωₘ::Real=20.` Maximum window size [m]
  * `slope::Real=0.01` Terrain slope [m/m]
  * `dhₘ::Real=2.5` Maximum elevation threshold [m]
  * `dh₀::Real=0.2` Initial elevation threshold [m]
  * `cellsize::Real=1.` Cellsize in [m]

[^zhang2003]: Zhang, Keqi, Shu-Ching Chen, Dean Whitman, Mei-Ling Shyu, Jianhua Yan, and Chengcui Zhang. “A Progressive Morphological Filter for Removing Nonground Measurements from Airborne LIDAR Data.” IEEE Transactions on Geoscience and Remote Sensing 41, no. 4 (2003): 872–82. [https://doi.org/10.1109/TGRS.2003.810682](https://doi.org/10.1109/TGRS.2003.810682).
