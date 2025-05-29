```
selection = select(addrs...)
```

Return a selection containing a given set of addresses.

Examples:

```julia
selection = select(:x, "foo", :y => 1 => :z)
selection = select()
selection = select(:x => 1, :x => 2)
```
