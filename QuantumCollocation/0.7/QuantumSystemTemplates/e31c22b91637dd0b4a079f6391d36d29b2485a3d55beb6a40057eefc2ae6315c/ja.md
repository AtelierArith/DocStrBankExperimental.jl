```
TransmonDipoleCoupling(
    g_ij::Float64,
    pair::Tuple{Int, Int},
    subsystem_levels::Vector{Int};
    lab_frame::Bool=false,
) -> QuantumSystemCoupling

TransmonDipoleCoupling(
    g_ij::Float64,
    pair::Tuple{Int, Int},
    sub_systems::Vector{QuantumSystem};
    kwargs...
) -> QuantumSystemCoupling
```

`QuantumSystemCoupling`オブジェクトをトランスモンキュービットのために返します。ラボフレームでは、ハミルトニアン結合項は

$$
H = g_{ij} (a_i + a_i^\dagger) (a_j + a_j^\dagger)
$$

回転フレームでは、ハミルトニアン結合項は

$$
H = g_{ij} (a_i a_j^\dagger + a_i^\dagger a_j)
$$

ここで、`a_i`は`i`番目のトランスモンの消滅演算子です。
