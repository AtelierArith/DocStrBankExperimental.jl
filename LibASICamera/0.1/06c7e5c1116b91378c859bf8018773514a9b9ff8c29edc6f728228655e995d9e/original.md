```
get_control_value(id::Integer, control_type::ASI_CONTROL_TYPE)
```

Fetches the current setting of the control value, e.g. exposure or gain.

# Args:

```
id: Camera id
control_type: The control type to fetch, e.g. exposure or gain.
```

# Returns:

```
A tuple (value, is_auto)
```

# Throws:

```
ASIError
```
