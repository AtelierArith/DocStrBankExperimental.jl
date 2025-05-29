```
split_model_binaries(model::EoSModel)::Vector{EoSModel}
```

多成分の `EoSModel` を与えると、すべてのバイナリモデルの組み合わせを含むリストを返します。

## 例

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
