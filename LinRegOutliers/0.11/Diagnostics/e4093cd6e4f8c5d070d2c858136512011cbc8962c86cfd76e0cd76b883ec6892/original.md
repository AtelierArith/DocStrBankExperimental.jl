```
dffits(setting)
```

Calculate `dffit` for all observations.

# Arguments

  * `setting::RegressionSetting`: A regression setting object.

# Examples

```julia-repl
julia> reg = createRegressionSetting(@formula(calls ~ year), phones);

julia> dffits(reg)
24-element Vector{Float64}:
   2.3008326745719785
   1.2189579001467337
   0.35535667547543426
  -0.14458523141740898
  -0.5558346324846752
  -0.8441316814464983
  -1.0329184407957257
  -1.16600692151232
  -1.2005633711667656
  -1.2549187193476428
  -1.3195581500053777
  -1.42383876236147
  -1.5917690629803474
  -1.6582086833534504
   2.7880619386124295
   3.1116532421969794
   4.367981450347031
   5.927603041427858
   8.442860517217582
  12.370243663029527
  -5.81610150322166
 -10.089153963127842
 -12.10803256546825
 -14.67006851119936
```

# References

Belsley, David A., Edwin Kuh, and Roy E. Welsch. Regression diagnostics:  Identifying influential data and sources of collinearity. Vol. 571. John Wiley & Sons, 2005.
