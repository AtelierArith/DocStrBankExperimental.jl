```
defcomp(comp_name::Symbol, ex::Expr)
```

Define a Mimi component `comp_name` with the expressions in `ex`.  The following  types of expressions are supported:

1. `dimension_name = Index()`   # defines a dimension
2. `parameter = Parameter(index = [dimension_name], units = "unit_name", default = default_value)`    # defines a parameter with optional arguments
3. `variable = Variable(index = [dimension_name], units = "unit_name")`    # defines a variable with optional arguments
4. `init(p, v, d)`              # defines an init function for the component
5. `run_timestep(p, v, d, t)`   # defines a run_timestep function for the component

Parses a @defcomp definition, converting it into a series of function calls that create the corresponding ComponentDef instance. At model build time, the ModelDef (including its ComponentDefs) will be converted to a runnable model.
