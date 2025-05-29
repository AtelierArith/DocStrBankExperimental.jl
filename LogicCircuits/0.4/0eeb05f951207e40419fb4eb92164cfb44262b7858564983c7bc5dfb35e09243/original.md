```
foldup_aggregate(node::LogicCircuit, 
    f_con::Function, 
    f_lit::Function, 
    f_a::Function, 
    f_o::Function, 
    ::Type{T})::T where T
```

Compute a function bottom-up on the circuit.  `f_con` is called on constant gates, `f_lit` is called on literal gates,  `f_a` is called on conjunctions, and `f_o` is called on disjunctions. Values of type `T` are passed up the circuit and given to `f_a` and `f_o` in an aggregate vector from the children.
