```
find_steady_state!(s::KPS4; prn=false, delta = 0.01, stiffness_factor=0.035, upwind_dir=-pi/2))
```

Find an initial equilibrium, based on the initial parameters `l_tether`, elevation and `v_reel_out`.
