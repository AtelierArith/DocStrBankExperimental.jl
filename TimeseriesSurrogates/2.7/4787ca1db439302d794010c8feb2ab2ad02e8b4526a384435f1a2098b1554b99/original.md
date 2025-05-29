```
PseudoPeriodicTwin(d::Int, τ::Int, δ = 0.2, ρ = 0.1, metric = Euclidean())
PseudoPeriodicTwin(δ = 0.2, ρ = 0.1, metric = Euclidean())
```

A pseudoperiodic twin surrogate[^Miralles2015], which is a fusion of the twin surrogate[^Thiel2006] and the pseudo-periodic surrogate[^Small2001].

## Input parameters

A delay reconstruction of the input timeseries is constructed using embedding dimension `d` and embedding delay `τ`. The threshold `δ ∈ (0, 1]` determines which points are "close" (neighbors) or not, and is expressed as a fraction of the attractor diameter, as determined by the input data. The authors of the original twin surrogate paper recommend `0.05 ≤ δ ≤ 0.2`[^Thiel2006].

If you have pre-embedded your timeseries, and timeseries is already a `::StateSpaceSet`, use the three-argument constructor (so that no delay reconstruction is performed). If you want a surrogate for a scalar-valued timeseries, use the five-argument constructor to also provide the embedding delay `τ` and embedding dimension `d`.

## Null hypothesis

Pseudo-periodic twin surrogates generate signals similar to the original data if the original signal is (quasi-)periodic. If the original signal is not (quasi-)periodic, then these surrogates will have different recurrence plots than the original signal, but preserve the overall shape of the attractor. Thus, `PseudoPeriodicTwin` surrogates can be used to test null hypothesis that the observed timeseries (or orbit) is consistent with a quasi-periodic orbit[^Miralles2015].

## Returns

A `d`-dimensional surrogate orbit (a `StateSpaceSet`) is returned. Sample the first column of this dataset if a scalar-valued surrogate is desired.

[^Small2001]: Small et al., Surrogate test for pseudoperiodic timeseries data, [Physical Review Letters, 87(18)](https://doi.org/10.1103/PhysRevLett.87.188101)

[^Thiel2006]: Thiel, Marco, et al. "Twin surrogates to test for complex synchronisation." EPL (Europhysics Letters) 75.4 (2006): 535.

[^Miralles2015]: Miralles, R., et al. "Characterization of the complexity in short oscillating timeseries: An application to seismic airgun detonations." The Journal of the Acoustical Society of America 138.3 (2015): 1595-1603.
