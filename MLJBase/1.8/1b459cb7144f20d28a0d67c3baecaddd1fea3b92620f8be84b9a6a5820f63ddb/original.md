```
last_model(mach::Machine)
```

Return the last model used to train the machine `mach`. This is a bona fide model, even if `mach.model` is a symbol.

Returns `nothing` if `mach` has not been trained.
