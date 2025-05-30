```
get_all_objects_of_type(type, workspace)
```

Get all objects of a specific type from the workspace.

# Arguments

  * `type::String`: The type of objects to retrieve (e.g. "GR", "RF", "SQ").
  * `workspace`: The workspace containing the objects.

# Returns

A named tuple where the keys are the names of the instances and the values are the objects.

# Example

```
GR = get_all_objects_of_type("GR", workspace)
GR.s_ex.str
```
