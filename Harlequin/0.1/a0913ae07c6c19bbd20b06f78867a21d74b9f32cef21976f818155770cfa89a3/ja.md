```
dipole_temperature(dir; params::DipoleParameters = DipoleParameters())
dipole_temperature(dir, freq_hz; params::DipoleParameters = DipoleParameters())
```

方向 `dir` に沿った双極子の温度を計算します。`dir` は、指向ベクトルの XYZ 成分を含む 3 要素の配列である必要があります。このベクトルは、`params` で双極子を指定するために使用されるベクトルと同じ座標系で表現されなければなりません。`params` は `DipoleParameters` 型のオブジェクトです。（ヒント：引数なしでコンストラクタを呼び出してこのオブジェクトを作成した場合、`DipoleParameters()` のように、黄道座標が使用されます。）

`freq_hz` が指定されている場合、相対論的な周波数依存の補正が適用されます。

# 参照

他の運動成分（例：宇宙船の運動によって引き起こされる軌道双極子）によって引き起こされる温度を計算する必要がある場合は、[`doppler_temperature`](@ref) を使用してください。

# 例

```julia
julia> dipole_temperature([0, 0, 1])
-0.0006532169921239991

julia> dipole_temperature([0, 0, 1], params=DipoleParameters(speed_m_s=371e3))
-0.0006548416782232279

julia> dipole_temperature([0, 0, 1], 30e9, params=DipoleParameters(speed_m_s=371e3))
-0.0006527515338213527
```
