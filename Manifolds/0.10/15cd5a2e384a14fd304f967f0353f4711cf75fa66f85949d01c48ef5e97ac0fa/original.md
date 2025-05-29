```
log(M::ProbabilitySimplex, p, q)
```

Compute the logarithmic map of `p` and `q` on the [`ProbabilitySimplex`](@ref) `M`.

$$
\log_pq = \frac{d_{Δ^n}(p,q)}{\sqrt{1-⟨\sqrt{p},\sqrt{q}⟩}}(\sqrt{pq} - ⟨\sqrt{p},\sqrt{q}⟩p),
$$

where $pq$ and $\sqrt{p}$ is meant elementwise.
