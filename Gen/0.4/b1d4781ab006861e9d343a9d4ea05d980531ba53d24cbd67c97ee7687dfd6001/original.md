```
set_submap!(choices::DynamicChoiceMap, addr, submap::ChoiceMap)
```

Replace the sub-assignment rooted at the given address with the given sub-assignment. Set the given value for the given address.

Will cause any previous value or sub-assignment at the given address to be deleted. It is an error if there is already a value present at some prefix of address.
