```
model_count(root::LogicCircuit, num_vars_in_scope::Int = num_variables(root))::BigInt
```

Get the model count of the circuit.  The `num_vars_in_scope` is set to number of variables in the circuit, but sometimes need to set different values,  for example, if not every variable is mentioned in the circuit.
