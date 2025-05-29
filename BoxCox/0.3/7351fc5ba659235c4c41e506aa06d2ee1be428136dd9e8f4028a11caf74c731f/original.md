```
boxcox(λ; atol=0)
boxcox(λ, x; atol=0)
```

Compute the Box-Cox transformation of x for the parameter value λ.

The Box-Cox transformation is defined as:

$$
\begin{cases}
\frac{x^{\lambda} - 1}{\lambda} &\quad \lambda \neq 0 \\
\log x &\quad \lambda = 0
\end{cases}
$$

for positive $x$. (If $x <= 0$, then $x$ must first be translated to be strictly positive.)

`atol` controls the absolute tolerance for treating λ as zero.

The one argument variant curries and creates a one-argument function of `x` for the given λ.

See also [`BoxCoxTransformation`](@ref).

# References

Box, George E. P.; Cox, D. R. (1964). "An analysis of transformations". *Journal of the Royal Statistical Society*, Series B. 26 (2): 211–252.
