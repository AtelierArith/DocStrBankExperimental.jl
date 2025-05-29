```
Chairmarks.DEFAULTS
```

A global constant that holds default benchmarking parameters.

When a parameter is unspecified it defaults to the value stored in `Chairmarks.DEFAULTS`.

Currently there is one stable default: `Chairmarks.DEFAULTS.seconds::Float64` which defaults to 0.1; and one experimental default: `Chairmarks.DEFAULTS.gc::Bool` which defaults to `true`.

All default values may be changed in the future and the `gc` default may be removed entirely.
