Macro for defining an agent struct. Expects a struct definition as argument.

The macro does 3 things:

1. It adds all baseline fields, defined in `AGENT_BASELINE_FIELDS` (the agent context `context`, the role handler `role_handler`, and the `aid`)
2. It adds the supertype `Agent` to the given struct.
3. It applies [`@with_def`](@ref) for default construction, the baseline fields are assigned to default values

# Example

For example the usage could like this.

```julia
@agent struct MyAgent
	my_own_field::String
end

# results in

@with_def mutable struct MyAgent <: Agent
	# baseline fields...
	my_own_field::String
    my_own_field_with_default::String = "Default"
end

# so you would construct your agent like this

my_agent = MyAgent("own value", my_own_field_with_default="OtherValue")
```
