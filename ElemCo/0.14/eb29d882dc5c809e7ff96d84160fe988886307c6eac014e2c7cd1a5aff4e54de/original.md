```
@cc(method, kwargs...)
```

Run coupled cluster calculation.

The type of the method is determined by the first argument (ccsd/ccsd(t)/dcsd etc).   The method can be specified as a string or as a variable, e.g.,    `@cc CCSD` or `@cc "CCSD"` or `ccmethod="CCSD";  @cc ccmethod`.

# Keyword arguments

  * `fcidump::String`: fcidump file (default: "", i.e., use integrals from `EC`).
  * `occa::String`: occupied α orbitals (default: "-").
  * `occb::String`: occupied β orbitals (default: "-").

The occupation strings can be given as a `+` separated list, e.g. `occa = 1+2+3` or equivalently `1-3`.    Additionally, the spatial symmetry of the orbitals can be specified with the syntax `orb.sym`, e.g. `occa = "-5.1+-2.2+-4.3"`.

# Examples

```julia
geometry="bohr
O      0.000000000    0.000000000   -0.130186067
H1     0.000000000    1.489124508    1.033245507
H2     0.000000000   -1.489124508    1.033245507"
basis = Dict("ao"=>"cc-pVDZ", "jkfit"=>"cc-pvtz-jkfit", "mpfit"=>"cc-pvdz-mpfit")
@dfhf
@dfints
@cc ccsd
```
