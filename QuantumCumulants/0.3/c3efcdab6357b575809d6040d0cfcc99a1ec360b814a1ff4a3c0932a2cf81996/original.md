```
MeanfieldEquations <: AbstractMeanfieldEquations
```

Type defining a system of differential equations, where `lhs` is a vector of derivatives and `rhs` is a vector of expressions. In addition, it keeps track of the Hamiltonian, the collapse operators and the corresponding decay rates of the system.

# Fields

*`equations`: Vector of the differential equations of averages. *`operator_equations`: Vector of the operator differential equations. *`states`: Vector containing the averages on the left-hand-side of the equations. *`operators`: Vector containing the operators on the left-hand-side of the equations. *`hamiltonian`: Operator defining the system Hamiltonian. *`jumps`: Vector of operators specifying the decay processes. *`jumps`: Vector of operators specifying the adjoint of the decay processes. *`rates`: Decay rates corresponding to the `jumps`. *`iv`: The independent variable (time parameter) of the system. *`varmap`: Vector of pairs that map the averages to time-dependent variables.     That format is necessary for ModelingToolkit functionality. *`order`: The order at which the [`cumulant_expansion`](@ref) has been performed.
