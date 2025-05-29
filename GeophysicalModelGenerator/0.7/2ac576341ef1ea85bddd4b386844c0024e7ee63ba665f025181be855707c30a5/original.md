```
Data::ParaviewData = read_data_PVTR(fname, dir)
```

Reads a parallel, rectilinear, `*.vts` file with the name `fname` and located in `dir` and create a 3D `Data` struct from it.

# Example

```julia-repl
julia> Data = read_data_PVTR("Haaksbergen.pvtr", "./Timestep_00000005_3.35780500e-01/")
ParaviewData
  size  : (33, 33, 33)
  x     ϵ [ -3.0 : 3.0]
  y     ϵ [ -2.0 : 2.0]
  z     ϵ [ -2.0 : 0.0]
  fields: (:phase, :density, :visc_total, :visc_creep, :velocity, :pressure, :temperature, :dev_stress, :strain_rate, :j2_dev_stress, :j2_strain_rate, :plast_strain, :plast_dissip, :tot_displ, :yield, :moment_res, :cont_res)
```
