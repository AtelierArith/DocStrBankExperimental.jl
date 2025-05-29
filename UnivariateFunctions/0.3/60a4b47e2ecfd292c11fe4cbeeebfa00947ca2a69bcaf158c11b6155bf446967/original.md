```
change_base_of_PE_Function(f::PE_Function, new_base::Real)
```

This changes the base of a `PE_Function`. So if the base was 2 then it can be converted to 3 with an additional constant term.

### Inputs

  * `f` - A `PE_Function`.
  * `new_base` - The new base.

### Returns

  * A `PE_Function` or a `Sum_Of_Functions`.
