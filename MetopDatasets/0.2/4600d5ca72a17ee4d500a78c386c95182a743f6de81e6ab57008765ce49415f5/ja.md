```
brightness_temperature(I::T, wavenumber::Real, default=T(NaN)) where T <: Real
```

IASI L1C スペクトルを放射から輝度温度に変換します。波数はメートル^-1 である必要があります。

# 例

```julia-repl
julia> file_path = "test/testData/IASI_xxx_1C_M01_20240819103856Z_20240819104152Z_N_C_20240819112911Z"
julia> ds = MetopDataset(file_path);
julia> spectrum = ds["gs1cspect"][:,1,1,1]
julia> wavenumber = ds["spectra_wavenumber"][:, 1]
julia> # 放射から輝度温度に変換
julia> T_B = brightness_temperature.(spectrum, wavenumber)
```
