```
Data::ParaviewData = read_data_PVTR(fname, dir)
```

`fname`という名前の並列直交`*.vts`ファイルを`dir`にある場所から読み込み、3D `Data`構造体を作成します。

# 例

```julia-repl
julia> Data = read_data_PVTR("Haaksbergen.pvtr", "./Timestep_00000005_3.35780500e-01/")
ParaviewData
  size  : (33, 33, 33)
  x     ϵ [ -3.0 : 3.0]
  y     ϵ [ -2.0 : 2.0]
  z     ϵ [ -2.0 : 0.0]
  fields: (:phase, :density, :visc_total, :visc_creep, :velocity, :pressure, :temperature, :dev_stress, :strain_rate, :j2_dev_stress, :j2_strain_rate, :plast_strain, :plast_dissip, :tot_displ, :yield, :moment_res, :cont_res)
```
