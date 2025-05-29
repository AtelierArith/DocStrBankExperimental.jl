Scoped value that captures the active context.

To pack / unpack in a given context `ctx::Context`, you can use this pattern:

```julia
using Base.ScopedValues

with(StructPack.context => ctx) do
  # Do your packing / unpacking without passing ctx explicitly
  # ...
end
```

!!! info
    Prior to julia 1.11, this constant was a global reference.

