`set_parameters!(calc, parameters) -> calc_new`

The returned `calc_new` may be a mutated `calc` or a new object. The caller  should not assume that `calc_new` is the same object as `calc`. This allows  for non-mutating implementations of `set_parameters!`.
