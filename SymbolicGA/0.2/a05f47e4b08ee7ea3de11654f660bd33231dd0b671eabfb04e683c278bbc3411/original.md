```
@geometric_space name sig quote
  n = 1.0::e4 + 1.0::e5
  n̄ = (-0.5)::e4 + 0.5::e5
  ... # other definitions
end [warn_override = true]
```

Generate a macro `@name` which defines a geometric space with signature `sig` along with optional user-provided definitions.

The resulting macro will have two methods:

  * `@name ex`, which acts as a standard `@ga sig ex` (but with potential extra definitions).
  * `@name T ex` which wraps the result into type `T`, just like `@ga sig T ex` would (see [`@ga`](@ref)).

If definitions are provided as an `Expr`, they will be parsed into [`Bindings`](@ref) and added to the default bindings. If definitions already are [`Bindings`](@ref), they will be used as is. `warn_override` can be set to false if you purposefully intend to purposefully override some of the default bindings.
