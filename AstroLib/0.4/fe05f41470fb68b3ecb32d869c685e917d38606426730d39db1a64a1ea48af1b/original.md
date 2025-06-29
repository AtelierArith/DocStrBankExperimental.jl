```
paczynski(u) -> amplification
```

### Purpose

Calculate gravitational microlensing amplification of a point-like source by a single point-like lens.

### Explanation

Return the [gravitational microlensing](https://en.wikipedia.org/wiki/Gravitational_microlensing) amplification of a point-like source by a single point-like lens, using Paczyński formula

$$
A(u) = \frac{u^2 + 2}{u\sqrt{u^2 + 4}}
$$

where $u$ is the projected distance between the lens and the source in units of [Einstein radii](https://en.wikipedia.org/wiki/Einstein_radius).

In order to speed up calculations for extreme values of $u$, the following asyntotic expressions for $A(u)$ are used:

$$
A(u) =
\begin{cases}
 1/u & |u| ≪ 1 \\
 \text{sgn}(u) & |u| ≫ 1
\end{cases}
$$

### Arguments

  * `u`: projected distance between the lens and the source, in units of Einstein radii

### Output

The microlensing amplification for the given distance.

### Example

Calculate the microlensing amplification for $u = 10^{-10}, 10^{-1}, 1, 10, 10^{10}$:

```jldoctest
julia> paczynski.([1e-10, 1e-1, 1, 10, 1e10])
5-element Vector{Float64}:
  1.0e10
 10.037461005722337
  1.3416407864998738
  1.0001922892047386
  1.0
```

### Notes

The expression of $A(u)$ of microlensing amplification has been given by Bohdan Paczyński in

  * Paczynski, B. 1986, ApJ, 304, 1. DOI:[10.1086/164140](http://dx.doi.org/10.1086/164140), Bibcode:[1986ApJ...304....1P](http://adsabs.harvard.edu/abs/1986ApJ...304....1P)

The same expression was actually found by Albert Einstein half a century earlier:

  * Einstein, A. 1936, Science, 84, 506. DOI:[10.1126/science.84.2188.506](http://dx.doi.org/10.1126/science.84.2188.506), Bibcode:[1936Sci....84..506E](http://adsabs.harvard.edu/abs/1936Sci....84..506E)
