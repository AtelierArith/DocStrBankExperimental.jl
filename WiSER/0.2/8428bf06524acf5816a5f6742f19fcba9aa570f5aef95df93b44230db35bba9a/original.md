```
rvarlmm(Xs::Array{Matrix}, Zs::Array{Matrix},
Ws::Array{Matrix}, β::Vector, τ::Vector;
respdist = MvNormal, Σγ=[], Σγω=[])
```

Generate a simulated response from the `WSVarLmmModel` based on:

  * `Xs`: array of each clusters `X`: mean fixed effects covariates
  * `Zs`: array of each clusters `Z`: random location effects covariates
  * `Ws`: array of each clusters `W`: within-subject variance fixed effects covariates
  * `β`: mean fixed effects vector
  * `τ`: within-subject variance fixed effects vector
  * `respdist`: the distribution for response. Default is MvNormal.
  * `Σγ`: random location effects covariance matrix.
  * `Σγω`: joint random location and random scale effects covariance matrix (if generating from full model)

Output is an array of simulated responses that match the ordering in `Xs, Zs, Ws`.

---

```
rvarlmm!(meanformula::FormulaTerm, reformula::FormulaTerm, 
wsvarformula::FormulaTerm, idvar::Union{Symbol, String},
datatable, β::Vector, τ::Vector; respdist = MvNormal, Σγ=[], Σγω=[],
respname::Symbol = :y)
```

Generate a simulated response from the VarLMM model based on a DataFrame `datatable`.  Note: **the datatable MUST be ordered by grouping variable for it to generate in the correct order. This can be checked via `datatable == sort(datatable, idvar)`. The response is based on:

  * `meanformula`: represents the formula for the mean fixed effects `β` (variables in X matrix)
  * `reformula`: represents the formula for the mean random effects γ (variables in Z matrix)
  * `wsvarformula`: represents the formula for the within-subject variance fixed effects τ (variables in W matrix)
  * `idvar`: the id variable for groupings.
  * `datatable`: DataFrame for the model. For this function it **must be in order**.
  * `β`: mean fixed effects vector
  * `τ`: within-subject variance fixed effects vector
  * `respdist`: the distribution for response. Default is MvNormal.
  * `Σγ`: random location effects covariance matrix.
  * `Σγω`: joint random location and random scale effects covariance matrix (if generating from full model)
  * `respname`: symbol representing the simulated response variable name.

`rvarlmm!()` produces a column in the datatable representing the new response.  It also returns the column `y` as a vector.  The datatable **must** be ordered by the ID variable for generated responses to match.
