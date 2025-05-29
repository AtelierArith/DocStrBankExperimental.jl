```
calculate_cleaned_map!(obs_list, destriping_data; comm=nothing, unseen=missing)
```

Provided a set of baselines in `baselines`, this function cleans the TOD in `obs_list` and computes the I/Q/U maps, which are saved in `destriping_data`.
