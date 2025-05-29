```
predict(M::HeteroPCAModel, x::AbstractVector; λ = 0.0)
```

Project a **single observation vector** `x` onto the estimated factor space, handling missing entries by solving a weighted least‑squares problem on the observed coordinates only.

`λ` adds a small ridge (Tikhonov) regularisation to keep the system well‑posed when fewer than `rank` coordinates are observed.
