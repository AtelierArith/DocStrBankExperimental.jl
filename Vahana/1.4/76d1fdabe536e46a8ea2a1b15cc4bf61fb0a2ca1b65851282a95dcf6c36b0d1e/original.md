```
set_param!(sim::Simulation, param::Symbol, value)
```

Assign the specified `value` to the `param` parameter. This operation is only allowed prior to calling the `finish_init!` method.

A pipeable version of `set_param!` is also available.
