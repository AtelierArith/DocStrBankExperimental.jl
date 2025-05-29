```
beta_statistic(Y::StateSpaceSet, s::Vector) [, τs, w]) → β
```

Compute the β-statistic `β` for input state space trajectory `Y` and a timeseries `s` according to Nichkawde [^Nichkawde2013], based on estimating derivatives on a projected manifold. For a range of delay values `τs`, `β` gets computed and its maximum over all considered `τs` serves as the optimal delay considered in this embedding cycle.

Arguments `τs, w` as in [`mdop_embedding`](@ref).

## Description

The `β`-statistic is based on the geometrical idea of maximal unfolding of the reconstructed attractor and is tightly related to the False Nearest Neighbor method ([^Kennel1992]). In fact the method eliminates the maximum amount of false nearest neighbors in each embedding cycle. The idea is to estimate the absolute value of the directional derivative with respect to a possible new dimension in the reconstruction process, and with respect to the nearest neighbor, for all points of the state space trajectory:

ϕ'(τ) = Δϕ*d(τ) / Δx*d

Δx*d is simply the Euclidean nearest neighbor distance for a reference point with respect to the given Theiler window `w`. Δϕ*d(τ) is the distance of the reference point to its nearest neighbor in the one dimensional time series `s`, for the specific τ. Δϕ_d(τ) = |s(i+τ)-s(j+τ)|, with i being the index of the considered reference point and j the index of its nearest neighbor.

Finally,

`β` = log β(τ) = ⟨log₁₀ ϕ'(τ)⟩ ,

with ⟨.⟩ being the mean over all reference points. When one chooses the maximum of `β` over all considered τ's, one obtains the optimal delay value for this embedding cycle. Note that in the first embedding cycle, the input state space trajectory `Y` can also be just a univariate time series.

[^Nichkawde2013]: Nichkawde, Chetan (2013). [Optimal state-space reconstruction using derivatives on projected manifold. Physical Review E 87, 022905](https://doi.org/10.1103/PhysRevE.87.022905).

[^Kennel1992]: Kennel, M. B., Brown, R., Abarbanel, H. D. I. (1992). [Determining embedding dimension for state-space reconstruction using a geometrical construction. Phys. Rev. A 45, 3403](https://doi.org/10.1103/PhysRevA.45.3403).
