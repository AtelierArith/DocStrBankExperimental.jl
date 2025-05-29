```
Parameters([mod::Module])
```

When creating an instance of `Parameters`, optionally one can specify the module in which parameter expressions will be evaluated. This only matters if there are any link parameters that depend on custom functions or global variables/constants. In this case, the `mod` argument should be the module in which these definitions exist.
