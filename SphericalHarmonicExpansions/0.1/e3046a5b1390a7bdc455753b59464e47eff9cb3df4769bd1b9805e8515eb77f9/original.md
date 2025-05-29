```
sphericalHarmonicsExpansion(Clm::SphericalHarmonicCoefficients, x::Variable, y::Variable, z::Variable)
```

*Description:*  Calculation of the spherical or solid harmonics expansion in Cartesian coordinates                 for given coefficients which define the maximum degree of the spherical harmonics
*Input:*  `Clm`       - Array with coefficients (length = (l+1)², l = max. deg. of the spherical harmonics)
          `x, y, z`   - Cartesian coordinates
*Output:*  Spherical/Solid harmonics expansion
