```
compute_ρ_sfc(thermo_params, ts_in, T_sfc)
```

表面の空気の密度を計算します。これは、表面の温度 T*sfc、気候の熱力学的状態 ts*in、および一連の Clima.Thermodynamics パラメータ thermo_params を考慮しています。

これは、理想気体の法則と静水圧平衡を仮定して表面に外挿します。
