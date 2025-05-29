```
kraus_evolve(
    kraus_ops :: Vector{<:AbstractMatrix},
    ρ :: Matrix
) :: Matrix
```

Kraus演算子`kraus_ops`を適用して密度演算子`ho`を進化させます。進化した状態$\rho'$は次のように構築されます。

$$
    \rho' = \sum_{i} K_{i} \rho K_{i}^{\dagger}
$$

ここで$K_i$はKraus演算子です。
