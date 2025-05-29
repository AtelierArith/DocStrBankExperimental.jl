```julia
partialderivatives_δPδlev_geosfp(geosfp; default_lev)

```

Return a function to calculate coefficients to multiply the `δ(u)/δ(lev)` partial derivative operator by to convert a variable named `u` from δ(u)/δ(lev)`to`δ(u)/δ(P)`, i.e. from vertical level number to pressure in hPa. The return format is`coordinate*index => conversion*factor`.
