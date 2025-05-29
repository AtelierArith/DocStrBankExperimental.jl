Manual albedo field, to be used with `set!` and is copied into the diagnostic variables on every time step. Defined so that parameterizations can change the albedo at every time step (e.g. snow cover) without losing the information of the original surface albedo. Fields are

  * `albedo::Any`
