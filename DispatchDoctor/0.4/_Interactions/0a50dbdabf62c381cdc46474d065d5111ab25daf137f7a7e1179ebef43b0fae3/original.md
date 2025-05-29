```
register_macro!(macro_name::Symbol, behavior::MacroInteractions)
```

Register a macro with a specified behavior in the `MACRO_BEHAVIOR` list.

This function adds a new macro and its associated behavior to the global list that tracks how macros should be treated when encountered during the stabilization process. The behavior can be one of `CompatibleMacro`, `IncompatibleMacro`, or `DontPropagateMacro`, which influences how the `@stable` macro interacts with the registered macro.

The default behavior for `@stable` is to assume `CompatibleMacro` unless explicitly declared.

# Arguments

  * `macro_name::Symbol`: The symbol representing the macro to register.
  * `behavior::MacroInteractions`: The behavior to associate with the macro, which dictates how it should be handled.

# Examples

```julia
using DispatchDoctor: register_macro!, IncompatibleMacro

register_macro!(Symbol("@mymacro"), IncompatibleMacro)
```
