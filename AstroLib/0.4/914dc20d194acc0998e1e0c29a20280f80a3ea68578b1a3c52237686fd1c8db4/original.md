```
uvbybeta(by, m1, c1, n[, hbeta=NaN, eby_in=NaN]) -> te, mv, eby, delm0, radius
```

### Purpose

Derive dereddened colors, metallicity, and Teff from Stromgren colors.

### Arguments

  * `by`: Stromgren b-y color
  * `m1`: Stromgren line-blanketing parameter
  * `c1`: Stromgren Balmer discontinuity parameter
  * `n`: Integer which can be any value between 1 to 8, giving approximate stellar classification.

    1. B0 - A0, classes III - V, 2.59 < Hbeta < 2.88,-0.20 <   c0   < 1.00
    2. B0 - A0, class   Ia     , 2.52 < Hbeta < 2.59,-0.15 <   c0   < 0.40
    3. B0 - A0, class   Ib     , 2.56 < Hbeta < 2.61,-0.10 <   c0   < 0.50
    4. B0 - A0, class   II     , 2.58 < Hbeta < 2.63,-0.10 <   c0   < 0.10
    5. A0 - A3, classes III - V, 2.87 < Hbeta < 2.93,-0.01 < (b-y)o < 0.06
    6. A3 - F0, classes III - V, 2.72 < Hbeta < 2.88, 0.05 < (b-y)o < 0.22
    7. F1 - G2, classes III - V, 2.60 < Hbeta < 2.72, 0.22 < (b-y)o < 0.39
    8. G2 - M2, classes  IV - V, 0.20 < m0    < 0.76, 0.39 < (b-y)o < 1.00
  * `hbeta` (optional): H-beta line strength index. If it is not supplied, then by default its value will be `NaN` and the code will estimate a value based on by, m1,and c1. It is not used for stars in group 8.
  * `eby_in` (optional): specifies the E(b-y) color to use. If not supplied, then by default its value will be `NaN` and E(b-y) will be estimated from the Stromgren colors.

### Output

  * `te`: approximate effective temperature
  * `mv`: absolute visible magnitude
  * `eby`: color excess E(b-y)
  * `delm0`: metallicity index, delta m0, may not be calculable for early B stars and so returns `NaN`.
  * `radius`: stellar radius (R/R(solar))

### Example

Determine the stellar parameters of 5 stars given their Stromgren parameters

```jldoctest
julia> using AstroLib

julia> by = [-0.001, 0.403, 0.244, 0.216, 0.394];

julia> m1 = [0.105, -0.074, -0.053, 0.167, 0.186];

julia> c1 = [0.647, 0.215, 0.051, 0.785, 0.362];

julia> hbeta = [2.75, 2.552, 2.568, 2.743, 0];

julia> nn = [1, 2, 3, 7, 8];

julia> uvbybeta.(by, m1, c1, nn, hbeta)
5-element Vector{NTuple{5, Float64}}:
 (13057.535222326893, -0.27375469585031265, 0.04954396423248884, -0.008292894218734928, 2.7136529525371897)
 (14025.053834219656, -6.907050783073221, 0.4140562248995983, NaN, 73.50771722263974)
 (18423.76405400214, -5.935816553877892, 0.2828247876690783, NaN, 39.84106215808709)
 (7210.507090112837, 2.2180408083364167, 0.018404079180028038, 0.018750927360588615, 2.0459018065648165)
 (5755.671513413262, 3.9449408311022, -0.025062997393370458, 0.03241423718769865, 1.5339239690774464)
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
