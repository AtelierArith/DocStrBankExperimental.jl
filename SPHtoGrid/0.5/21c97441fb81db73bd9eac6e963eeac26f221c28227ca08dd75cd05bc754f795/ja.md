```
write_smac2_par(x, y, z,
                euler_angle_0, euler_angle_1, euler_angle_2,
                xy_size, z_depth, xy_pix::Integer,
                input_file, output_file, path,
                effect_module::Integer=0, effect_flag::Integer=0,
                ν_obs::Real=1.44e9, cosmology::Integer=0,
                CR_pmin::Real=10.0, CR_pmax::Real=1.e7)
```

P-Smac2パラメータファイルを書き込みます。まだすべての関連パラメータは実装されていません！
