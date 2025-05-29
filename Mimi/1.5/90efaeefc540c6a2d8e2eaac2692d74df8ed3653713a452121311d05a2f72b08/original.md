```
defcomposite(cc_name, ex)
```

Define a Mimi CompositeComponentDef `cc_name` with the expressions in `ex`. Expressions are all shorthand for longer-winded API calls, and include the following:

```
p = Parameter(...)
v = Variable(varname)
local_name = Component(name)
Component(name)  # equivalent to `name = Component(name)`
connect(...)
```

Variable names are expressed as the component id (which may be prefixed by a module, e.g., `Mimi.adder`) followed by a `.` and the variable name in that component. So the form is either `modname.compname.varname` or `compname.varname`, which must be known in the current module.

Unlike leaf components, composite components do not have user-defined `init` or `run_timestep` functions; these are defined internally to iterate over constituent components and call the associated method on each.
