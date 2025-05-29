```
function ClimaLand.turbulent_fluxes!(
    dest,
    atmos::PrescribedAtmosphere,
    model::CanopyModel,
    Y::ClimaCore.Fields.FieldVector,
    p::NamedTuple,
    t,
)
```

大気との間で乱流フラックスを計算するためのキャノピー特有の関数です。潜熱フラックス、顕熱フラックス、水蒸気フラックス、および空気抵抗を返します。

キャノピーは水蒸気と顕熱フラックスに対して異なる抵抗を必要とするため、src/shared_utilities/drivers.jlのデフォルトバージョンを使用することはできません。また、抵抗はustarに依存しており、これをSurfaceFluxesを使用して計算した後、これらの抵抗を考慮して調整する必要があります。
