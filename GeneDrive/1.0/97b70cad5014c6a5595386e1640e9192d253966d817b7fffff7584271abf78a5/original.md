```
update_population_size(stages::DataStructures, Stage}, new_popsize::Int64)
```

Return updated population size. Note: `new_popsize` argument refers specifically to the Female population; if e.g. new_popsize = 500, the full adult population (Females and Males) will be 500*2.
