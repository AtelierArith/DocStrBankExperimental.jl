```
run_filt(traj::Traj, ins::INS, meas, itp_mapS,
         filt_type::Vector{Symbol}; ...)
```

Run multiple filter models and print results (nothing returned).

**Arguments:**

  * `filt_type`: multiple filter types, e.g., [`:ekf`,`:ekf_online_nn`]
