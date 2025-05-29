```
`update!(:: AbstractState; convert = false, kwargs...)`
```

Generic update function for the State The function compares the kwargs and the entries of the State. If the type of the kwargs is the same as the entry, then it is updated.

Set kargs `convert` to true to update even incompatible types.

Examples: `update!(state1)` `update!(state1, current_time = 2.0)` `update!(state1, convert = true, current_time = 2.0)`

See also: `GenericState`, `reinit!`, `update_and_start!`, `update_and_stop!`
