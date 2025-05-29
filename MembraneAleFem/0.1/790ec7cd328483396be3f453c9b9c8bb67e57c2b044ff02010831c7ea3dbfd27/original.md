```
Params
```

Parameters that must be specified for any simulation.

For [`Scenario`](@ref)-specific data that must be included via keyword arguments, see [`check_params`](@ref MembraneAleFem.check_params). The following information is contained:

  * `motion::`[`Motion`](@ref)     → type of motion
  * `scenario::`[`Scenario`](@ref) → type of scenario
  * `num1el::Int64`   → number of elements in $ζ^1$
  * `num2el::Int64`   → number of elements in $ζ^2$
  * `output::Bool`    → write output (yes by default)
  * `length::Float64` → length, in real space
  * `kb::Float64`     → mean bending modulus
  * `kg::Float64`     → Gaussian bending modulus
  * `ζv::Float64`     → membrane viscosity
  * `pn::Float64`     → normal pressure (body force)
  * `poly::Int64`     → polynomial order of basis functions
  * `gp1d::Int64`     → number of Gauss points, in 1-D
  * `nders::Int64`    → number of 1-D B-spline derivatives
  * `nen::Int64`      → number of element nodes
  * `αdb::Float64`    → Dohrmann–Bochev parameter
  * `αm::Float64`     → mesh parameter
  * `εk::Float64`     → tolerance numerical calculation of matrix K
  * `εnr::Float64`    → Netwon–Raphson tolerance
