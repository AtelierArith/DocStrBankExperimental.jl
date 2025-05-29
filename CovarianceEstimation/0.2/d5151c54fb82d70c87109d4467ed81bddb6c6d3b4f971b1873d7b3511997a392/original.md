```
BiweightMidcovariance(; c=9.0, modify_sample_size=false)
```

The biweight midcovariance is a covariance estimator that is resilient to outliers.

The technique derives originally from astrophysics [1], and is implemented in the Python module [Astropy](https://www.astropy.org/) [2], as well as in NIST's Dataplot [3].

Consider two random variables $x$ and $y$, for which we have $n$ observations $\{(x_i, y_i)\}$. The biweight midcovariance is then defined to be:

$$
n_s\cdot\frac{
    \sum_{|u_i|<1,|v_i|<1}(x_i - M_x)(1 - u_i^2)^2(y_i - M_y)(1 - v_i^2)^2
}{
    \left(\sum_{|u_i|<1}(1 - u_i^2)(1-5u_i^2)\right)
    \left(\sum_{|v_i|<1}(1 - v_i^2)(1-5v_i^2)\right)
}
$$

where $n_s$ is the sample size, $M_x$ and $M_y$ are the medians of $\{x_i\}$ and $\{y_i\}$ respectively, and

$$
\begin{aligned}
u_i &= \frac{x_i - M_x}{c \cdot \mathrm{MAD}_x} \\
v_i &= \frac{y_i - M_y}{c \cdot \mathrm{MAD}_y},
\end{aligned}
$$

where $\mathrm{MAD}$ represents the median absolute deviation,

$$
\begin{aligned}
\mathrm{MAD}_x &= \mathrm{median}(\left\{\left|x_i - M_x\right|\right\}) \\
\mathrm{MAD}_y &= \mathrm{median}(\left\{\left|y_i - M_y\right|\right\}).
\end{aligned}
$$

If either $\mathrm{MAD}_x = 0$ or $\mathrm{MAD}_y = 0$, the pairwise covariance is defined to be zero.

The parameter $c$ is a tuning constant, for which the default is $9.0$. Larger values will reduce the number of outliers that are removed — i.e. reducing robustness, but increasing sample efficiency.

# Fields

  * `c::Float64`: The tuning constant corresponding to $c$ above.
  * `modify_sample_size::Bool`: If `false`, then we use a sample size $n_s$ equal to the   total number of observations $n$. This is consistent with the standard definition of   biweight midcovariance in the literature. Otherwise, we count only those elements which   are not rejected as outliers in the numerator, i.e. those for which $|u_i|<1$   and $|v_i|<1$.   This follows the implementation in astropy [2].

# Complexity

  * Space: $O(p^2)$
  * Time: $O(np^2)$

# References

[1] Beers, Flynn, and Gebhardt (1990; AJ 100, 32) "Measures of Location and Scale for Velocities in Clusters of Galaxies – A Robust Approach"

[2] [Astropy biweight_midcovariance](https://docs.astropy.org/en/stable/api/astropy.stats.biweight_midcovariance.html)

[3] [NIST Dataplot biweight midcovariance](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/biwmidc.htm)
