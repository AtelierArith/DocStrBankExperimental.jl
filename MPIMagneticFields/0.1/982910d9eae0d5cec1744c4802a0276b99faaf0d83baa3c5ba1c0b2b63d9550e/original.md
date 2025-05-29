```julia
value(field, args; kwargs...)

```

Retrieve the value of a magnetic field.

# The order of arguments varies depending on the traits of the actual type.

# With a time varying field, the first argument is the time `t`.

# Otherwise the position `r` is the first parameter.

# The rotation angle `ϕ` is the next parameter if the field is rotatable,

# otherwise it is the shift vektor `δ`.
