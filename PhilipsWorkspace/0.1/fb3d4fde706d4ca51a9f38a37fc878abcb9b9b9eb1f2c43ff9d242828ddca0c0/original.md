```
get_parameter_value(name, workspace)
```

Get the value of a parameter with the given name from the workspace.

The parameter values are typically stored as arrays with a single element so we recursively apply `only` to "unwrap" them.

# Arguments

  * `name::String`: The name of the parameter.
  * `workspace::Workspace`: The workspace containing the parameters.

# Returns

The "unwrapped" value of the parameter.

# Example

```
EX_PROTO_scan_enable = get_parameter_value("EX_PROTO_scan_enable", workspace)
```
