```
convert_flow_type_symbol(::Client, flow_type::Union{ForwardFlow,BackwardFlow})
```

This function converts a flow type (either ForwardFlow or BackwardFlow) into a symbol.  The conversion process involves converting the flow type to a string, removing parentheses,  adding an underscore before "Flow", converting to lowercase, and finally converting to a symbol.

# Arguments

  * `::Client`: The Client object.
  * `flow_type::Union{ForwardFlow,BackwardFlow}`: The flow type to be converted.

# Returns

  * A Symbol representing the flow type.

# Examples

```julia
client = Client()
flow_type = ForwardFlow()
flow_sym = convert_flow_type_symbol(client, flow_type)
```
