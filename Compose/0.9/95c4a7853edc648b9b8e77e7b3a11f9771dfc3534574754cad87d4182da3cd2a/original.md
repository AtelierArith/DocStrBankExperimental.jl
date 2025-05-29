```
fillopacity(value)
```

Define a fill opacity, where 0≤value≤1.  For svg, nested contexts  will inherit from parent contexts e.g. `(context(), fillopacity(a), (context(), fill(c::String), circle()))`.
