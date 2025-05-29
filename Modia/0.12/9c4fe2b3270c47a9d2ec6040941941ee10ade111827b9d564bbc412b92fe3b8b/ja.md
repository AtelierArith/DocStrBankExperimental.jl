```
stateSelectionFunctions = StateSelection.StateSelectionFunctions(;
    var_name               = v          -> nothing,
    var_julia_name         = v          -> nothing,
    var_unit               = v          -> "",
    var_startInitFixed     = v          -> (nothing,false),   # (startOrInit, fixed)
    var_is_state           = v_original -> false,
    equation               = e          -> ""
    isSolvableEquation     = (e_original,v_original) -> false,
    isLinearEquation       = (e_original,v_original) -> (false, false),
    getSolvedEquationAST   = (e, v)                  -> nothing,
    getResidualEquationAST = (e, residualName)       -> nothing,
    showMessage            = (message; severity=0,from="???",details="",variables=Int[],equations=Int[]) -> println("...")
)
```
