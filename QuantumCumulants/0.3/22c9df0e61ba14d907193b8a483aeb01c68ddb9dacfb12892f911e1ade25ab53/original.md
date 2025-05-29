```
CorrelationFunction(op1,op2,de0;steady_state=false,add_subscript=0,mix_choice=maximum)
```

The first-order two-time correlation function of two operators.

The first-order two-time correlation function of `op1` and `op2` evolving under the system `de0`. The keyword `steady_state` determines whether the original system `de0` was evolved up to steady state. The arguments `add_subscript` defines the subscript added to the name of `op2` representing the constant time.

Note that the correlation function is stored in the first index of the underlying system of equations.
