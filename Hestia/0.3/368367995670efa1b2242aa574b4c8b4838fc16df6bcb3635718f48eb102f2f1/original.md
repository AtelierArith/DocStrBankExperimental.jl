```
emit!(flux :: Vector{<:Real}, temperature :: Vector{<:Real}, emission :: Emission)
```

Calculates the right-hand side of the natural Robin boundary along a boundary for a given `Emission`.

$$
\Phi = -h ~ (\theta - \theta_{amb}) - \sigma ~ [\varepsilon_{1} ~ \theta^4 - \varepsilon_{2} ~ \theta_{amb}^4)]
$$

Note: in-place operation - results are saved in array `flux`.
