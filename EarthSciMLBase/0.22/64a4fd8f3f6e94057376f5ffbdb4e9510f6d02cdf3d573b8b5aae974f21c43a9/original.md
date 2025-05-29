Replace the parameter `p` in the system `sys` with a new variable that has the same name, units, and description as `p`.

```julia
param_to_var(sys, ps)

```

This can be useful to replace a parameter that does not change in time in a model component with one specified by another system that does change in time (or space). For example, the code below specifies a first-order loss equation, and then changes the temperature (which determines the loss rate) with a temperature value that varies in time.

```

```
