```
sublevelalias!(I::Ion, sublevel::Tuple{String,Real}, alias::String)
```

Assigns an alias `alias` to `sublevel` of `I`. This then allows one to pass `alias` in place of `sublevel` (for `I` only) into any function which accepts a sublevel as an argument.
