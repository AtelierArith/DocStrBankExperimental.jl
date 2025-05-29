```
submap = get_submap(choices::ChoiceMap, addr)
```

Return the sub-assignment containing all choices whose address is prefixed by addr.

It is an error if the assignment contains a value at the given address. If there are no choices whose address is prefixed by addr then return an `EmptyChoiceMap`.
