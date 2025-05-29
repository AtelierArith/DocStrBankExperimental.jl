```
struct CapacityConstraint <: Modification
```

**Capacity Constraint** - A Modification that applies a constraint based on total capacity. 

  * `name`: modification name
  * `table`: whether to apply the constraint to items in the gen or storage table.
  * `max_values`: maximum values for a year (defaults as an empty OrderedDict if no maxs)
  * `min_values`: minimum values for a year (defaults as an empty OrderedDict if no mins)
  * `table_filters`: OrderedDict of the table filters
