```
threshold(w::AbstractVector, q::Number, [method=:knockoff], [m::Int=1])
```

Chooses a threshold τ > 0 by choosing `τ` to be one of the following τ = min{ t > 0 : {#j: w[j] ≤ -t} / {#j: w[j] ≥ t} ≤ q }        (`method=:knockoff`) τ = min{ t > 0 : (1 + {#j: w[j] ≤ -t}) / {#j: w[j] ≥ t} ≤ q }  (`method=:knockoff`)

# Inputs

  * `w`: Vector of feature important statistics
  * `q`: target FDR (between 0 and 1)
  * `method`: either `:knockoff` or `:knockoff_plus` (default)
  * `rej_bounds`: Number of values of top W to consider (default = 10000)

# Reference:

Equation 3.10 (`method=:knockoff`) or 3.11 (`method=:knockoff_plus`) of  "Panning for Gold: Model-X Knockoffs for High-dimensional Controlled Variable Selection" by Candes, Fan, Janson, and Lv (2018)
