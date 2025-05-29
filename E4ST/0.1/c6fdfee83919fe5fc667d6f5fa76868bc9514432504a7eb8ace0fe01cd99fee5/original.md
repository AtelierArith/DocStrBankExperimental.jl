```
struct RunSequential <: Iterable

RunSequential(;years)
```

Runs E4ST sequentially by running `years` (or sets of years) one after another.  Overwrites `config[:years]`, throwing a warning if the first set in `iter` is different than that in the config.

  * `years = ["y2020", "y2025"]`: this will run E4ST twice, once for each year
  * `years = ["y2020", ["y2025", "y2030"]]`: this will run E4ST twice, once for `"y2020"` and once for `["y2025", "y2030"]`
