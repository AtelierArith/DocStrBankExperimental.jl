```
find_steady_state!(s::KPS3; prn=false, delta = 0.0, stiffness_factor=0.035, upwind_dir=-pi/2)
```

初期パラメータ `l_tether`、標高、`v_reel_out` に基づいて初期平衡を見つけます。
