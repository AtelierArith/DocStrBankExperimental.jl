```
reduced_operator(solver::RBSolver,feop::ParamOperator,args...;kwargs...) -> RBOperator
reduced_operator(solver::RBSolver,feop::TransientParamOperator,args...;kwargs...) -> TransientRBOperator
```

FE演算子 `feop` からRB演算子を計算します。
