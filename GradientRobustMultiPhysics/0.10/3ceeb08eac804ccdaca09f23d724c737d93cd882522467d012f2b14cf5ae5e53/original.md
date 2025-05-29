```
function PointEvaluator(FEB::FEVectorBlock, FEOP::AbstractFunctionOperator, action::AbstractAction = NoAction(); AT = ON_CELLS)
```

constructor for PointEvaluator that evaluate the given FEVectorBlock with the specified operator (possibly postprocessed by an action) at arbitrary points inside entities of the given assembly type
