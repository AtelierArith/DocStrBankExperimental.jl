```
value = get_value(choices::ChoiceMap, addr)
```

Return the value at the given address in the assignment, or throw a KeyError if no value exists. A syntactic sugar is `Base.getindex`:

```
value = choices[addr]
```
