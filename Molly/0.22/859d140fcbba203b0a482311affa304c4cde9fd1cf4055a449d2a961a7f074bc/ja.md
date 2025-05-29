```
MonteCarloMembraneBarostat(pressure, tension, temperature, boundary; n_steps=30,
                   n_iterations=1, scale_factor=0.01, scale_increment=1.1,
                   max_volume_frac=0.3, trial_find_neighbors=false,
                   xy_isotropy=false, z_axis_fixed=false, constant_volume=false)
```

圧力を制御するためのモンテカルロ膜バロスタット。

`xy_isotropy`フラグを`true`に設定すると、x軸とy軸を等方的にスケーリングします。`z_axis_fixed`フラグを`true`に設定すると、z軸を切り離して固定します。`constant_volume`フラグを`true`に設定すると、z軸を適切にスケーリングすることでシステムの体積を一定に保ちます。`z_axis_fixed`と`constant_volume`フラグは同時に`true`にすることはできません。

[Chow and Ferguson 1995](https://doi.org/10.1016/0010-4655(95)00059-O)、[Åqvist et al. 2004](https://doi.org/10.1016/j.cplett.2003.12.039)およびOpenMMソースコードを参照してください。定期的に、モンテカルロステップが試みられ、座標とバウンディングボックスがランダムに選ばれた軸でランダムに選ばれた量だけスケーリングされます。このステップは以下に基づいて受け入れられるか拒否されます。

$$
\Delta W = \Delta E + P \Delta V - \gamma \Delta A - N k_B T \ln \left( \frac{V + \Delta V}{V} \right)
$$

ここで、`ΔE`はポテンシャルエネルギーの変化、`P`は選択された軸に沿った平衡圧力、`ΔV`は体積の変化、`γ`は表面張力、`ΔA`は表面積の変化、`N`はシステム内の分子の数、`T`は平衡温度、`V`はシステムの体積です。`ΔW ≤ 0`の場合、ステップは常に受け入れられ、`ΔW > 0`の場合、ステップは確率`exp(-ΔW/kT)`で受け入れられます。

スケールファクターは、受け入れ率を約半分に保つために時間とともに修正されます。システムのトポロジーが設定されている場合、分子は単位として移動されるため、結合長などの特性は変化しません。

バロスタットは、シミュレーションが一定の温度で実行されていると仮定しますが、温度を積極的に制御するわけではありません。[`Langevin`](@ref)シミュレーターや[`AndersenThermostat`](@ref)カップリングなどの温度カップリング法と併用する必要があります。試行移動を行ったり、受け入れられた移動の後に隣接リストは更新されません。バロスタットはシステムのバウンディングボックスを変更することができることに注意してください。

このバロスタットは3Dシステムにのみ利用可能です。
