Macro for defining a role struct. Expects a struct definition as argument.

The macro does 3 things:

1. It adds all baseline fields, defined in `ROLE_BASELINE_FIELDS` (the role context)
2. It adds the supertype `Role` to the given struct.
3. It applies [`@with_def`](@ref) for default construction, the baseline fields are assigned to default values

For example the usage could like this.

```julia
@role struct MyRole
	my_own_field::String
end

# results in

@with_def mutable struct MyRole <: Role
	# baseline fields...
	my_own_field::String
    my_own_field_with_default::String = "Default"
end

# so youl would construct your role like this

my_roel = MyRole("own value", my_own_field_with_default="OtherValue")
```
