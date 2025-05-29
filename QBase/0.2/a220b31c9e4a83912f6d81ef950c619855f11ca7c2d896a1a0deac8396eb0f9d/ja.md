```
KrausChannel(
    kraus_ops :: Vector{Matrix{T}};
    atol=ATOL :: Float64
) :: KrausChannel{T}
```

量子チャネルのクローズ演算子表現。チャネルは密度演算子 $\rho$ を次のように進化させます。

$$
    \mathcal{N}(\rho) = \sum_{i} K_{i} \rho K_{i}^{\dagger},
$$

ここで、$\{K_i \in L(A,B)\}_i$ はクローズ演算子として知られる線形演算子の集合です。

`kraus_ops` が量子チャネルを構成しない場合、`DomainError` がスローされます。詳細については [`is_kraus_channel`](@ref) を参照してください。
