```
stepwisevif!(model::SDM, limit, tr=:;kwargs...)
```

Drops the variables with the largest variance inflation from the model, until all VIFs are under the threshold. The last positional argument (defaults to `:`) is the indices to use for the VIF calculation. All keyword arguments are passed to `train!`.
