```
set_control_value(id::Integer, control_type::ASI_CONTROL_TYPE, value, auto::Bool=false)
```

Sets a control (e.g. exposure) to the given value. Automatically sets the minimum or maximum if the given value is out of bounds.

# Args:

```
id: Camera id
control_type: The control type to set, e.g. exposure or gain.
value: The value to which the control is set.
auto: Whether or not the control should be automatically set.
    Check if this is supported for the given control beforehand.
```

# Throws:

```
ASIError
```
