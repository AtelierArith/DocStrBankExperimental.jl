```
struct GenerationConstraint <: Modification
```

**Generation Constraint** - A Modification that applies a constraint based on (yearly generation) * (a column from the gen table). 

  * `name`: modification name
  * `col`: gen table column
  * `max_values`: maximum values for a year (defaults as an empty OrderedDict if no maxs)
  * `min_values`: minimum values for a year (defaults as an empty OrderedDict if no mins)
  * `gen_filters`: OrderedDict of the generator filters
