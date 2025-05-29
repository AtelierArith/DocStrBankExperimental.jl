```
thermal_speed(T::EnergyOrTemp, mass::Mass, method::ThermalVelocityMethod = MostProbable(), ndim = 3)
```

マクスウェル分布を持つ粒子の熱運動の速度を計算します。

$$
v_{th} = C_o \sqrt{\frac{k_B T}{m}}
$$

ここで、$T$は分布に関連する温度、$m$は粒子の質量、$C_o$は比例定数です。 ```
