```
get_choices(trace)
```

Return a value implementing the assignment interface

Note that the value of any non-addressed randomness is not externally accessible.

Example:

```julia
choices::ChoiceMap = get_choices(trace)
z_val = choices[:z]
```
