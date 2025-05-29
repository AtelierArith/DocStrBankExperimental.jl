```
match_capacity!(data, model, table_name::Symbol, pcap_name::Symbol, name::Symbol, sets::Vector{Vector{Int64}})
```

Constrains `sets` of generator indices so that their `pcap_gen` values sum to the max and min specified in the first member of the set.  The names of the constraints are:

  * `Symbol("cons_pcap_max_$name")`
  * `Symbol("cons_pcap_min_$name")`
