```
doppler_temperature(velocity_m_s, dir, tcmb_k)
doppler_temperature(velocity_m_s, dir, tcmb_k, freq_hz)
```

運動によって引き起こされる温度を、ドップラー効果を通じて `velocity_m_s`（m/s単位の3ベクトル）によって計算します。`freq_hz` が指定されている場合、計算には四重極相対論的補正が含まれます。

# 参照

太陽系の運動によって引き起こされる太陽の双極子をCMB静止系に対して計算する必要がある場合は、[`dipole_temperature`](@ref)を使用する方が簡単です。

# 例

```
