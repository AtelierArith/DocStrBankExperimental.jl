```
is_invalid_startvalue(result::TrackerResult)
```

Returns `true` if the path tracking failed since the start value was invalid. You can inspect `result.return_code` to get the exact return code. Possible values if `is_invalid_startvalue(result) == true` are

  * `:terminated_invalid_startvalue_singular_jacobian` indicates that the Jacobian of the homotopy at the provided start value is singular, i.e., if it has not full-column rank.
  * `:terminated_invalid_startvalue` indicates that the the provided start value is not sufficiently close to a solution of the homotopy.
