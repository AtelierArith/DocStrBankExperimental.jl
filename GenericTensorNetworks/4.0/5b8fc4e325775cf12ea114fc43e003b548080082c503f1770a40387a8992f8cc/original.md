```
load_configs(filename; format=:binary, bitlength=nothing, num_flavors=2)
```

Load configurations from file `filename`. The format is `:binary` or `:text`. If the format is `:binary`, the bitstring length `bitlength` must be specified, `num_flavors` specifies the degree of freedom.
