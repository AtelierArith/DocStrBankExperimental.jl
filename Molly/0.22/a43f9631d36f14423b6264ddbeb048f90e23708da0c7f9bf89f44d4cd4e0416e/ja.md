```
MonteCarloAnisotropicBarostat(pressure, temperature, boundary; n_steps=30,
                   n_iterations=1, scale_factor=0.01, scale_increment=1.1,
                   max_volume_frac=0.3, trial_find_neighbors=false)
```

圧力を制御するためのモンテカルロ異方性バロスタット。

3Dシステムの場合、`pressure`は長さ3の`SVector`で、各軸のターゲット圧力を表すpressX、pressY、pressZの成分を持ちます。2Dシステムの場合、`pressure`は長さ2の`SVector`で、pressXとpressYの成分を持ちます。軸を固定するには、対応する圧力を`nothing`に設定します。

[Chow and Ferguson 1995](https://doi.org/10.1016/0010-4655(95)00059-O)、[Åqvist et al. 2004](https://doi.org/10.1016/j.cplett.2003.12.039)、およびOpenMMソースコードを参照してください。定期的に、モンテカルロステップが試みられ、座標とバウンディングボックスがランダムに選ばれた軸でランダムに選ばれた量だけスケーリングされます。このステップは次の式に基づいて受け入れられるか拒否されます。

$$
\Delta W = \Delta E + P \Delta V - N k_B T \ln \left( \frac{V + \Delta V}{V} \right)
$$

ここで、`ΔE`はポテンシャルエネルギーの変化、`P`は選択された軸に沿った平衡圧力、`ΔV`は体積の変化、`N`はシステム内の分子の数、`T`は平衡温度、`V`はシステムの体積です。`ΔW ≤ 0`の場合、ステップは常に受け入れられ、`ΔW > 0`の場合、ステップは確率`exp(-ΔW/kT)`で受け入れられます。

スケールファクターは、受け入れ率を約半分に維持するために時間とともに修正されます。システムのトポロジーが設定されている場合、分子はユニットとして移動されるため、結合長などの特性は変化しません。

バロスタットは、シミュレーションが一定の温度で実行されていると仮定しますが、温度を積極的に制御するわけではありません。[`Langevin`](@ref)シミュレーターや[`AndersenThermostat`](@ref)カップリングなどの温度カップリング法と併用する必要があります。試行移動を行う際や受け入れられた移動の後に隣接リストは更新されません。バロスタットはシステムのバウンディングボックスを変更する可能性があることに注意してください。
