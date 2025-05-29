```
@dfcc(method="svd-dcsd")
```

Run coupled cluster calculation using density fitted integrals.

The type of the method is determined by the first argument.   The method can be specified as a string or as a variable, e.g.,    `@dfcc SVD-DCSD` or `@dfcc "SVD-DCSD"` or `ccmethod="SVD-DCSD";  @dfcc ccmethod`.

# Examples

```julia
geometry="bohr
O      0.000000000    0.000000000   -0.130186067
H1     0.000000000    1.489124508    1.033245507
H2     0.000000000   -1.489124508    1.033245507"
basis = Dict("ao"=>"cc-pVDZ", "jkfit"=>"cc-pvtz-jkfit", "mpfit"=>"cc-pvdz-mpfit")
@dfhf
@dfcc svd-dcsd
```
