```
report_hyperparameters(save_dir::AbstractPath; prefix="SM_HP_")
```

Saves all hyperparameters to a JSON file named "hyperparameters.json" in the `save_dir` and prints each key-value pair to the logger.

The hyperparameters are taken from the cached `HYPERPARAMETERS` dictionary of all that were used, combined with any enviroment variables matching the prefix. Where things occur in both, the cached dictionary takes precedence. Hyperparameters read from enviroment variables are all recorded as strings. (You can overwrite this by using them via `hyperparam(type, name)` before the report)

The regex to extract the components is: `hyperparameters: (?<key>)=(?<value>)`.
