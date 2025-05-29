```
assemble(operator, test_functions, trial_functions;
    storage_policy = Val{:bandedstorage},
    threading = Threading{:multi},
    quadstrat=defaultquadstrat(operator, test_functions, trial_functions))
```

Assemble the system matrix corresponding to the operator `operator` tested with the test functions `test_functions` and the trial functions `trial_functions`.
