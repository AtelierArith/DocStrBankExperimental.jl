```
KruskalWallisTest(groups::AbstractVector{<:Real}...)
```

Perform Kruskal-Wallis rank sum test of the null hypothesis that the `groups` $\mathcal{G}$ come from the same distribution against the alternative hypothesis that that at least one group stochastically dominates one other group.

The Kruskal-Wallis test is an extension of the Mann-Whitney U test to more than two groups.

The p-value is computed using a $χ^2$ approximation to the distribution of the test statistic $H_c=\frac{H}{C}$:

$$
    \begin{align*}
    H & = \frac{12}{n(n+1)} \sum_{g ∈ \mathcal{G}} \frac{R_g^2}{n_g} - 3(n+1)\\
    C & = 1-\frac{1}{n^3-n}\sum_{t ∈ \mathcal{T}} (t^3-t),
    \end{align*}
$$

where $\mathcal{T}$ is the set of the counts of tied values at each tied position, $n$ is the total number of observations across all groups, and $n_g$ and $R_g$ are the number of observations and the rank sum in group $g$, respectively. See references for further details.

Implements: [`pvalue`](@ref)

# References

  * Meyer, J.P, Seaman, M.A., Expanded tables of critical values for the Kruskal-Wallis H statistic. Paper presented at the annual meeting of the American Educational Research Association, San Francisco, April 2006.

# External links

  * [Kruskal-Wallis test on Wikipedia ](https://en.wikipedia.org/wiki/Kruskal-Wallis_one-way_analysis_of_variance)
