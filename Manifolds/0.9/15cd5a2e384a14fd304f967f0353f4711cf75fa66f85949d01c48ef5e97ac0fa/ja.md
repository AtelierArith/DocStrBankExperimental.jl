```
log(M::ProbabilitySimplex, p, q)
```

確率単純体 [`ProbabilitySimplex`](@ref) `M` における `p` と `q` の対数写像を計算します。

$$
\log_pq = \frac{d_{Δ^n}(p,q)}{\sqrt{1-⟨\sqrt{p},\sqrt{q}⟩}}(\sqrt{pq} - ⟨\sqrt{p},\sqrt{q}⟩p),
$$

ここで $pq$ と $\sqrt{p}$ は要素ごとに意味します。
