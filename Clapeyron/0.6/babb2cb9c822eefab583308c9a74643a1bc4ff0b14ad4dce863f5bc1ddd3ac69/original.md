```
split_model_binaries(model::EoSModel)::Vector{EoSModel}
```

Given a multicomponent `EoSModel`, returns a list with the combination of all binary models.

## Example

```julia-repl
julia> model = PCPSAFT(["water", "methanol", "propyleneglycol","methyloxirane"])
PCPSAFT{BasicIdeal} with 4 components:
 "water"
 "methanol"
 "propyleneglycol"
 "methyloxirane"
Contains parameters: Mw, segment, sigma, epsilon, dipole, dipole2, epsilon_assoc, bondvol

julia> split_model_binaries(model)
6-element Vector{PCPSAFT{BasicIdeal}}:
 PCPSAFT{BasicIdeal}("water", "methanol")
 PCPSAFT{BasicIdeal}("water", "propyleneglycol")
 PCPSAFT{BasicIdeal}("water", "methyloxirane")
 PCPSAFT{BasicIdeal}("methanol", "propyleneglycol")
 PCPSAFT{BasicIdeal}("methanol", "methyloxirane")
 PCPSAFT{BasicIdeal}("propyleneglycol", "methyloxirane")
```
