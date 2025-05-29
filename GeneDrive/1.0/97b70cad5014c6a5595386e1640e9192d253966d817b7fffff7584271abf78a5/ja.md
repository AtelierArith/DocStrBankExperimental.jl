```
update_population_size(stages::DataStructures, Stage}, new_popsize::Int64)
```

更新された個体群サイズを返します。注意: `new_popsize` 引数は特に雌の個体群を指します; 例えば、new_popsize = 500 の場合、全体の成体個体群（雌と雄）は 500*2 になります。
