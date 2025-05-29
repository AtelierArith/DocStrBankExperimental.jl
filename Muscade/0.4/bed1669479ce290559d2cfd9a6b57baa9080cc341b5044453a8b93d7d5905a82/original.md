```
state = setdof!(state,value        ;[class=:X],field=:somefield,                  [order=0])
state = setdof!(state,value::Vector;[class=:X],field=:somefield,nodID=[nodids...],[order=0])
```

Set the value of dofs of the same class and field, at various nodes and for various states. There are two methods:

1. A single `value` is applied to all relevant nodes in the model
2. `value` and `nodID` are vectors of the same lengths, and each element in `value` is applied to the corresponding node.

`setdof!` is peculiar in that it modifies its input `state` variable, but must be used as a function. A call like `stateout = setdof!(statein,value;class=:X,field=:somefield,order=1)` can turn out in two ways: If the `state` already stores derivatives in `X` to order 1, then `statein` is mutated and `statein===stateout`. Otherwise, `statein` is unchanged, `stateout` is a new object, sharing as much memory as possible with `statein`. To avoid confusion, always use the syntax shown above.

See also: [`getresult`](@ref), [`addnode!`](@ref), [`solve`](@ref)
