```
assign_migration!(network::Network, migration_data::Dict, species::Type{<:Species})
```

Return `Network` instance with `migration` field populated by user-specified transition rates.

# Note to user:

  * Input data must be formatted as a nested dictionary. First level denotes relevant life stage and gene, second level includes to/from nodes and transition rate.
  * Stage and gene combinations not specified by input data retain a default transition rate of zero.
