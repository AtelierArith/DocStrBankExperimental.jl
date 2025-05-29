```julia
kinetic_energy(u, setup; kwargs...) -> Any

```

運動エネルギー場 $k$ を計算します（インプレースバージョン）。`interpolate_first` が true の場合、次のように与えられます。

$$
k_I = \frac{1}{8} \sum_\alpha (u^\alpha_{I + h_\alpha} + u^\alpha_{I - h_\alpha})^2.
$$

そうでない場合、次のように与えられます。

$$
k_I = \frac{1}{4} \sum_\alpha ((u^\alpha_{I + h_\alpha})^2 + (u^\alpha_{I - h_\alpha})^2),
$$

[Sanderse2023](@cite) のように。

微分可能なバージョン。
