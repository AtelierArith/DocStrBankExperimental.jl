```
XPRS_HEURDIVERANDOMIZE
```

The level of randomization to apply in the diving heuristic. The diving heuristic uses priority weights on rows and columns to determine the order in which to e.g. round fractional columns, or the direction in which to round them. (double)

This control determines by how large a random factor these weights should be changed.

Default value: `0.0`

Values: 0.0-1.0 : Amount of randomization (0.0=none, 1.0=full)
