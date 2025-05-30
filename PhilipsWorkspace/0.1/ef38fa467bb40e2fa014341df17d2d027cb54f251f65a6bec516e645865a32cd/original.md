```
get_object(type, instance, workspace)
```

Extracts attribute names and values for a specific object instance in a workspace.

# Arguments

  * `type::String`: The type of the object (e.g. "GR", "RF", "SQ").
  * `instance::String`: The instance of the object (e.g. "s_ex", "ex", "base").
  * `workspace::Workspace`: The GOAL workspace.

# Returns

A named tuple with attribute names as symbols and attribute values.

# Example

```
GR_s_ex = get_object("GR", "s_ex", workspace)
GR_s_ex.str
```
