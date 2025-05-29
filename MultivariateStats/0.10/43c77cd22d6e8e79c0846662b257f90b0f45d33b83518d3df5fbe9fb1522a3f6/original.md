```
ccasvd(Zx, Zy, xmean, ymean, p)
```

Compute CCA based on singular value decomposition of centralized sample matrices `Zx` and `Zy`, and return [`CCA`](@ref) model[^1].

Parameters:

  * `Zx`: The centralized sample matrix for `X`.
  * `Zy`: The centralized sample matrix for `Y`.
  * `xmean`: The mean vector of the **original** samples of `X`, which can be

a vector of length `dx`, or an empty vector indicating a zero mean.

  * `ymean`: The mean vector of the **original** samples of `Y`, which can be

a vector of length `dy`, or an empty vector indicating a zero mean.

  * `p`: The output dimension, *i.e* the dimension of the common space.
