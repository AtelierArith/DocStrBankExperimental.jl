```
IMEXTableau(; a_exp, b_exp, c_exp, a_imp, b_imp, c_imp)
```

A wrapper for an IMEX Butcher tableau (or, more accurately, a pair of Butcher tableaus, one for explicit tendencies and the other for implicit tendencies). Only `a_exp` and `a_imp` are required arguments; the default values for `b_exp` and `b_imp` assume that the algorithm is FSAL (first same as last), and the default values for `c_exp` and `c_imp` assume that it is internally consistent.

The explicit tableau must be strictly lower triangular, and the implicit tableau must be lower triangular (only DIRK algorithms are currently supported).
