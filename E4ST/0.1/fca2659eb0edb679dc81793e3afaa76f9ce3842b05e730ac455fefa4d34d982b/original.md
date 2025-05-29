```
read_num_params!(config, data) ->
```

Any parameter specified as a numeric in the config will be added to `data`. This is so that parameters with a single value (i.e. VOLL, ng*upstream*ch4_leakage) can be tracked and accessed easily in data. 
