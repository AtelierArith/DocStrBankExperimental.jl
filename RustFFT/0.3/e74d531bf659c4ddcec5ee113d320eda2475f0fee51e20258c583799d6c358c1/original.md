```
new_planner(::Type{ComplexF32})
new_planner(::Type{ComplexF64})
```

Returns a new planner. By default each plan creates a new planner but one can also be provided to the `plan_*`-functions as a keyword argument: `rustfft_planner`. By reusing the same planner, internal data is reused across different plans saving memory and setup time.
