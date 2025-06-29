```
modifyfield!(value, name::Symbol, op, x, [order::Symbol]) -> Pair
modifyfield!(value, i::Int, op, x, [order::Symbol]) -> Pair
```

These atomically perform the operations to get and set a field after applying the function `op`.

```
y = getfield(value, name)
z = op(y, x)
setfield!(value, name, z)
return y => z
```

If supported by the hardware (for example, atomic increment), this may be optimized to the appropriate hardware instruction, otherwise it'll use a loop.
