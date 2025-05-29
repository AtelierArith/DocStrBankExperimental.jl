```
@reinitialize model
```

Process the changes made to a model and prepare the model instance for analysis.  Call this macro after all changes to parameters, variable names, shock names,  equations, autoexogenize lists, and removed steadystate equations have been declared and defined.

Additional/new steadystate constraints can be added after the call to `@reinitialize`.
