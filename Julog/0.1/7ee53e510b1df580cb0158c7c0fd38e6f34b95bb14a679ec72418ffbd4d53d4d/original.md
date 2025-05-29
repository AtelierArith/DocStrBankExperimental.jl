```
eval_term(term, env[, funcs])
```

Given an environment, evaluate all variables in a Julog term to constants. Returns a term that is as fully evaluated as possible.

# Arguments

  * `term::Term`: A term to evaluate.
  * `env::Dict{Var,Term}`: An environment mapping variables to terms.
  * `funcs::Dict=Dict()`: Additional custom functions (e.g. custom math).
