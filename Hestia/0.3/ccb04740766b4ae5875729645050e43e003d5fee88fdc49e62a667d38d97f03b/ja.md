```
emit(temperature :: Real, emission :: Emission)
```

与えられた `Emission` に対する境界条件の右辺を計算します。

$$
\Phi = -h ~ (\theta - \theta_{amb}) - \sigma ~ [\varepsilon_{1} ~ \theta^4 - \varepsilon_{2} ~ \theta_{amb}^4)]
$$
