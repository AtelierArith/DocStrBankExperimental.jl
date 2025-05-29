```
set_value!(choices::DynamicChoiceMap, addr, value)
```

Set the given value for the given address.

Will cause any previous value or sub-assignment at this address to be deleted. It is an error if there is already a value present at some prefix of the given address.

The following syntactic sugar is provided:

```
choices[addr] = value
```
