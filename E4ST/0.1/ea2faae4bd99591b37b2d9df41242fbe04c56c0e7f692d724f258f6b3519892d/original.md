```
add_build_constraints!(data, model, table_name, pcap_name)
```

Adds constraints to the model for:

  * `cons_<pcap_name>_prebuild` - Constrain Capacity to 0 before the start/build year
  * `cons_<pcap_name>_noadd` - Constrain existing capacity to only decrease (only retire, not add capacity)
  * `cons_<pcap_name>_exog` - Constrain unbuilt exogenous generators to be built to pcap0 in the first year after year_on
  * `cons_<pcap_name>_match_min_build` - Constrain minimum capacity of generators at the same site to add up to the >= minimum capacity.
  * `cons_<pcap_name>_match_min_build` - Constrain minimum capacity of generators at the same site to add up to the <= maximum capacity.
