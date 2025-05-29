```
on_new_rule(hook, frule | rrule)
```

Register a `hook` function to run when new rules are defined. The hook receives a signature type-type as input, and generally will use `eval` to define an overload of an AD system's overloaded type For example, using the signature type `Tuple{typeof(+), Real, Real}` to make `+(::DualNumber, ::DualNumber)` call the `frule` for `+`. A signature type tuple always has the form: `Tuple{typeof(operation), typeof{pos_arg1}, typeof{pos_arg2}...}`, where `pos_arg1` is the first positional argument.

The hooks are automatically run on new rules whenever a package is loaded. They can be manually triggered by [`refresh_rules`](@ref). When a hook is first registered with `on_new_rule` it is run on all existing rules.
