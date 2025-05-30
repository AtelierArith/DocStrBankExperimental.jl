```
emit!(flux :: Vector{<:Real}, temperature :: Vector{<:Real}, emission :: Emission)
```

与えられた `Emission` に対して、境界に沿った自然ロビン境界の右辺を計算します。

$$
\Phi = -h ~ (\theta - \theta_{amb}) - \sigma ~ [\varepsilon_{1} ~ \theta^4 - \varepsilon_{2} ~ \theta_{amb}^4)]
$$

注意: インプレース操作 - 結果は配列 `flux` に保存されます。
