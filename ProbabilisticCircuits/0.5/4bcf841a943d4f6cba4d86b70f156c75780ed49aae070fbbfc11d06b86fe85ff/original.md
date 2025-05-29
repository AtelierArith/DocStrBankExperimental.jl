```
loglikelihood(root::ProbCircuit, data::Matrix, example_id; Float=Float32)
```

Computes marginal loglikelihood recursively on cpu for a single instance `data[example_id, :]`.

**Note**: Quite slow, only use for demonstration/educational purposes. 
