```
B = smf(A; ω, slope, dhₘ, dh₀, cellsize)
```

Applies the simple morphological filter by *Pingel et al. (2013)* [^pingel2013] to `A`.

# Output

  * `B::Array{Float64,2}` A filtered version of A

# Arguments

  * `A::Array{T,2}` Input Array
  * `ω::Float64=18.` Maximum window size [m]
  * `slope::Float64=0.01` Terrain slope [m/m]
  * `cellsize::Float64=1.` Cellsize in [m]

[^pingel2013]: Pingel, Thomas J., Keith C. Clarke, and William A. McBride. 2013. ‘An Improved Simple Morphological Filter for the Terrain Classification of Airborne LIDAR Data’. ISPRS Journal of Photogrammetry and Remote Sensing 77 (March): 21–30. [https://doi.org/10.1016/j.isprsjprs.2012.12.002](https://doi.org/10.1016/j.isprsjprs.2012.12.002).
