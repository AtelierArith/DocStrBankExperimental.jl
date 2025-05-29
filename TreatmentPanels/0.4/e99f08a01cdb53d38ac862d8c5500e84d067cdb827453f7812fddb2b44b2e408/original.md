```
decompose_y(x <: BalancedPanel)

Decomposes the outcome matrix Y into four elements:

* Pre-treatment outcomes for treated units (y₁₀)
* Post-treatment outcomes for treated units (y₁₁)
* Pre-treatment outcomes for control units (y₀₀)
* Post-treatment outcomes for treated units (y₀₁)

and returns a tuple (y₁₀, y₁₁, y₀₀, y₀₁)
```
