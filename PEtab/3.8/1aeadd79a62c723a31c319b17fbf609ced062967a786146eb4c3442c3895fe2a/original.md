```
PEtabEvent(condition, affects, targets)
```

A model event triggered by `condition` that sets the value of `targets` to that of `affects`.

For a collection of examples with corresponding plots, see the documentation.

## Arguments

  * `condition`: A Boolean expression that triggers the event when it transitions from   `false` to `true`. For example, if `t == c1`, the event is triggered when the model   time `t` equals `c1`. For `S > 2.0`, the event triggers when specie `S` passes 2.0   from below.
  * `affects`: An equation of of model species and parameters that describes the effect of   the event. It can be a single expression or a vector if there are multiple targets.
  * `targets`: Model species or parameters that the event acts on. Must match the dimension   of `affects`.
