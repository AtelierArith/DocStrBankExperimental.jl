```
tmle(dataset; 
    estimands="factorialATE", 
    estimators="glmnet"; 
    verbosity=0, 
    outputs=Outputs(),
    chunksize=100,
    rng=123,
    cache_strategy="release-unusable",
    sort_estimands=false
)
```

TMLE CLI.

# Args

  * `dataset`: Data file (either .csv or .arrow)

# Options

  * `--estimands`: A string ("factorialATE") or a serialized TMLE.Configuration (accepted formats: .json | .yaml | .jls)
  * `--estimators`: A julia file containing the estimators to use.
  * `-v, --verbosity`: Verbosity level.
  * `-o, --outputs`: Ouputs to be generated.
  * `--chunksize`: Results are written in batches of size chunksize.
  * `-r, --rng`: Random seed (Only used for estimands ordering at the moment).
  * `-c, --cache-strategy`: Caching Strategy for the nuisance functions, any of ("release-unusable", "no-cache", "max-size").

# Flags

  * `-s, --sort_estimands`: Sort estimands to minimize cache usage (A brute force approach will be used, resulting in exponentially long sorting time).
