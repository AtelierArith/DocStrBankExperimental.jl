```
add_fano_noise(E_dep::RealQuantity, E_ionisation::RealQuantity, f_fano::Real)::RealQuantity
```

エネルギー沈着 `E_dep` にファノノイズを追加します。これは、検出器材料のイオン化エネルギー `E_ionisation` とファノ因子 `f_fano` を仮定しています。

## 引数

  * `E_dep::RealQuantity`: 半導体材料に沈着したエネルギー。
  * `E_ionisation`: 半導体材料で1つの電子-ホール対を生成するのに必要なエネルギー。
  * `f_fano`: 材料のファノ因子。

## 例

```julia
add_fano_noise(100u"keV", 2.95u"eV", 0.129)
```

いくつかの材料特性は `SolidStateDetectors.material_properties` に保存されており、ここで使用できます：

```julia
material = SolidStateDetectors.material_properties[:HPGe]
add_fano_noise(100u"keV", material.E_ionisation, material.f_fano)
```

!!! note
    `E_dep` または `E_ionisation` に単位付きの値を使用するには、パッケージ [Unitful.jl](https://github.com/PainterQubits/Unitful.jl) が必要です。

