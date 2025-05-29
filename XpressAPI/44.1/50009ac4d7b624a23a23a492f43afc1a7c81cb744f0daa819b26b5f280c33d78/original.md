```
XPRS_GLOBALSPATIALBRANCHCUTTINGEFFORT
```

Limits the effort that is spent on creating cuts during spatial branching. (double)

Default value: -1.0

Values: -1 : The algorithm chooses the effort limit automatically (default). 0 : Disables cuts on branching entities. 0<n<1 : Relative effort to spend on cutting on branching entities. Higher values lead to more cuts.
