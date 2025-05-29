```
struct EmissionCap <: Policy
```

Emission Cap - A limit on a certain emission for a given set of generators.

  * `name`: name of the policy (Symbol)
  * `emis_col`: name of the emission rate column in the gen table (ie. emis_co2) (Symbol)
  * `targets`: OrderedDict of cap targets by year
  * `gen_filters`: OrderedDict of generator filters
  * `gen_cons`: GenerationConstraint Modification created on instantiation of the EmissionCap (not specified in config). It sets the cap targets as the max_targets of the GenerationConstraint and passes on other fields.
