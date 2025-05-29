```
compute_residuals!(residuals, baseline_lengths, destriping_data, obs_list; comm=nothing, unseen=missing)
```

この関数は、[`destripe!`](@ref)で実装された共役勾配アルゴリズムの開始時に$A x - b$の値を計算するために使用されます。
