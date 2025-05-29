```
iau_1976_prec(jd1, jd2)
```

IAU 1976 precession angles

# Arguments

  * `date1::Float64`: Starting date of precession (in TDB)
  * `date1::Float64`: Ending date of precession (in TDB)

# Returns

  * `angles::Tuple{AbstractFloat}`: precession angles ζ, z, θ (in radians)

The rotation matrix is Rz(-z)Ry(θ)Rz(-ζ).

The accumulated precession angles are valid for a limited time span. The absolute accuracy of the present formulation is <0.1 arcsec for 1960AD - 2040AD, <1 arcsec for 1640AD - 2360AD, and <3 arcsec for 500BC - 3000AD. The errors are >10 arcsec outside of 1200BC - 3900AD.
