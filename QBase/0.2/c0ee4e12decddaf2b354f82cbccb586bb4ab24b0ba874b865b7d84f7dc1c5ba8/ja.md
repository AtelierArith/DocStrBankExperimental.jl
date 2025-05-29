```
depolarizing_channel( ρ :: State, μ :: Real ) :: State
```

デポラライジングチャネルは、量子状態 `ρ` に均一な古典ノイズを混合します。引数 `μ` は、量子状態に混合されるノイズの量を表します。量子状態 $\rho$ に対して、デポラライジングチャネルは次のように表されます：

$$
    \mathcal{D}_{\mu}(\rho) = \mu \rho + \frac{(1 - \mu)}{d}\mathbb{I}_d
$$

`μ` が `1 ≥ μ ≥ 0` を満たさない場合、`DomainError` がスローされます。
