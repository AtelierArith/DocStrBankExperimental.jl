```
calculate_cleaned_map!(obs_list, destriping_data; comm=nothing, unseen=missing)
```

`baselines`に基づいて、この関数は`obs_list`内のTODをクリーンアップし、I/Q/Uマップを計算します。これらは`destriping_data`に保存されます。
