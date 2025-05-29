```
requiresMeshConnectivityFor(meshName::String)::Bool
```

Checks if the given mesh requires connectivity.

preCICE may require connectivity information from the solver and ignores any API calls regarding connectivity if it is not required. Use this function to conditionally generate this connectivity.
