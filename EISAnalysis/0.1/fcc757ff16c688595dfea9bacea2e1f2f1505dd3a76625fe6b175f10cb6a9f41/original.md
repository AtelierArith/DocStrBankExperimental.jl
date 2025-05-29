```
print_circuit(circuit)
```

Prints the elements of a circuit along with its parameters

# Arguments

  * `circuit::Circuit`: The circuit being printed

# Examples

```julia
using EISAnalysis
eval(initialize())
randles_circuit = 0.23r-r/0.2q
print_circuit(randles_circuit)

# output 

0.23r
1.0r
0.2 * q ^ 0.8
```
