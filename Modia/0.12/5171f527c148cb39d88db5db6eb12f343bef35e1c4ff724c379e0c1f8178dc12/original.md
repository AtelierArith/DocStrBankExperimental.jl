```
xe_info = StateElementInfo(x_name, x_name_julia, der_x_name, der_x_name_julia,
                           stateCategory, unit, startOrInit, fixed, nominal, unbounded;
                           startIndex=-1, x_segmented_startIndex=-1)
```

Return an instance of the mutable struct `StateElementInfo` that defines the information for one element of the state vector.

# Arguments

  * x_name: Name of x-element or "" if no name (if stateCatebory = XLAMBDA or XMUE)
  * x*name*julia: Julia name of x-element in getDerivatives!/getResiduals! function or "" if not needed (since no code generation).
  * der*x*name: Name of der*x-element or "" if either `der(x*name)` or if no name (if stateCategory = XALG).
  * der*x*name*julia: Julia name of der*x-element in getDerivatives!/getResiduals! function or "" if not needed (since no code generation).
  * stateCategory::StateCategory: Category of the state
  * unit: unit of XD, XALG (x*name) or XLAMBDA, XMUE (der*x_name) or "" if not yet known)
  * startOrInit: Start or init value (scalar or vector)
  * fixed: false (= guess value) or true (= not changed by initialization).        Only relevant for ode=false, otherwise ignored.
  * nominal: Nominal value (NaN if determined via startOrInit value)
  * unbounded: false or true
  * startIndex: = -1, if not yet known. startIndex with respect to x.
  * x*segmented*startIndex: =-1, if not yet known. startIndex with respect to x_segmented.
