```
opf_results(m::JuMP.AbstractModel, net::Network)
```

For all the symbols in `net.var_names` fill in a dictionary of variable values using the same structure as the model variable containers.
