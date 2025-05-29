```
reduced_operator(solver::RBSolver,feop::ParamOperator,args...;kwargs...) -> RBOperator
reduced_operator(solver::RBSolver,feop::TransientParamOperator,args...;kwargs...) -> TransientRBOperator
```

Computes a RB operator from the FE operator `feop`
