```
npa2sdp(expr, moment; eq=[], ge=[])
```

Generate the NPA relaxation for a given quantum optimisation problem.

The main purpose of this function is to eliminate equality constraints from the input problem. This function also takes a representation of the real part of the input problem, if it isn't already real-valued.

The return value is a tuple containing 1) the expression to optimise, and 2) a vector of matrices that will be required to be positive semidefinite. The first element of the vector is derived from the input moment matrix; any additional ones are derived from any additional inequality constraints provided.

# Arguments

  * `expr`: the operator whose expectation value we want to optimise.
  * `moment`: the moment matrix
  * `eq`=[] and `ge=[]`: vectors of operators whose expectation values we want to set equal to and lower bound by zero, respectively.
