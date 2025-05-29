```
iterate!(iter::RunSequential, config, data) -> nothing
```

Iterates by:

  * Incrementing the years in the config
  * Changing the `config[:out_path]` to be `"iter<n>"`
  * Changing `config[:gen_file]`
