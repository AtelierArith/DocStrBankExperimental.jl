```
get_parameter_group(group, workspace)
```

Get all parameters in a specific group from the workspace.

# Arguments

  * `group::String`: The name of the parameter group.
  * `workspace::Workspace`: The workspace containing the parameters.

# Returns

A named tuple containing the parameter names and their values.

# Example

```
EX_PROTO = get_parameter_group("EX_PROTO", workspace)
EX_PROTO.scan_enable
```
