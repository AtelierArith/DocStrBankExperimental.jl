```
normalize(s, n; <keyword arguments>)
```

Normalize.

# Arguments

  * `s::AbstractVector`
  * `n::Real=1.0`
  * `method::Symbol`:

      * `:zscore`: by z-score
      * `:minmax`: in [-1, +1]
      * `:log`: using log-transformation
      * `:log10`: using log10-transformation
      * `:neglog`: using -log-transformation
      * `:neglog10`: using -log10-transformation
      * `:neg`: in [-∞, 0]
      * `:pos`: in [0, +∞]
      * `:perc`: in percentages
      * `:gauss`: to Gaussian
      * `:invroot`: to inverse root: 1/sqrt(x)
      * `:n`: in [0, n], default is [0, 1]
      * `:softmax`: using softmax function: exp(x_i) / sum(exp(x))
      * `:sigmoid`: using sigmoid function: 1 /  1 + exp(-x_i)
      * `:mad`: by MAD
      * `:rank`: using tiedranks
      * `:none`

# Returns

  * `normalized::AbstractVector`
