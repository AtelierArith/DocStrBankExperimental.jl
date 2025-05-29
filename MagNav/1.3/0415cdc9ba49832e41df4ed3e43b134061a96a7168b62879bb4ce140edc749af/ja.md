```
run_filt(traj::Traj, ins::INS, meas, itp_mapS,
         filt_type::Vector{Symbol}; ...)
```

複数のフィルタモデルを実行し、結果を出力します（何も返されません）。

**引数:**

  * `filt_type`: 複数のフィルタタイプ、例：[`:ekf`,`:ekf_online_nn`]
