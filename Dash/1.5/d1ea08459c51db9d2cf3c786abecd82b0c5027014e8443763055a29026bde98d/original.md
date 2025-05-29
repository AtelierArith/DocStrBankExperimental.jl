```
dcc_interval(;kwargs...)
```

An Interval component A component that repeatedly increments a counter `n_intervals` with a fixed time delay between each increment. Interval is good for triggering a component on a recurring basis. The time delay is set with the property "interval" in milliseconds.

  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `disabled` (Bool; optional): If True, the counter will no longer update
  * `interval` (optional): This component will increment the counter `n_intervals` every

`interval` milliseconds

  * `max_intervals` (optional): Number of times the interval will be fired.

If -1, then the interval has no limit (the default) and if 0 then the interval stops running.

  * `n_intervals` (optional): Number of times the interval has passed
