```
get_params(a::Union{CircuitElement,Circuit})
```

Gets the parameters for elements in a circuit.

# Attributes

  * `a::Union{CircuitElement,Circuit}`: The circuit or circuit element

# Examples

```julia
using EISAnalysis
eval(initialize())
randles_circuit = 0.23r-(r-0.025wo^80)/0.2q
get_params(randles_circuit)

# output

4-element Vector{Any}:
 0.23
 1.0
  (0.025, 80.0)
  (0.2, 0.8)
```
