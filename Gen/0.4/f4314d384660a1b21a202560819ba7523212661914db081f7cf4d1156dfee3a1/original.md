```
Selection
```

Abstract type for selections of addresses.

All selections implement the following methods:

```
Base.in(addr, selection)
```

Is the address selected?

```
Base.getindex(selection, addr)
```

Get the subselection at the given address.

```
Base.isempty(selection)
```

Is the selection guaranteed to be empty?

```
get_address_schema(T)
```

Return a shallow, compile-time address schema, where `T` is the concrete type of the selection.
