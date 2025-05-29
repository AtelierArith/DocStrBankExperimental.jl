```
project(M::ProbabilitySimplex, p)
```

project `p` from the embedding onto the [`ProbabilitySimplex`](@ref) `M`. The formula reads

$$
\operatorname{proj}_{Δ^n}(p) = \frac{1}{⟨\mathbb 1,p⟩}p,
$$

where $\mathbb 1 ∈ ℝ$ denotes the vector of ones. Not that this projection is only well-defined if $p$ has positive entries.
