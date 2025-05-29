```
@mutt struct MyType
    fields...
end
```

Macro to define a *mutable-until-shared* data type. Mutable-until-shared types are essentially immutable data structures, that give the flexibility of mutating them until they are "finished", at which point they are free to be shared with other Tasks, or other parts of the code.

`Mutt` types act like mutable structs, until the user calls `mark_immutable!(obj)`, after which they act like purely immutable types.

The complete API includes:

  * [`mark_immutable!(obj)`](@ref): Freeze `obj`, preventing any future mutations.
  * [`branch!(obj)`](@ref): Make a *mutable* shallow copy of `obj`.
  * [`mutable_version(obj)`](@ref): Return a mutable version of `obj`, either `obj` itself if already mutable, or a [`branch!`ed](@ref branch!) copy.
  * [`branchactions(obj::Mutt)`](@ref): Users can override this callback for their type with any actions that need to occur when it is branched.

This macro modifies the definition of `S` to include an extra first parameter: `__mutt_mutable :: Bool`, which tracks at runtime when the value becomes immutable. Inner constructors are handled automatically, so you not need to construct this generated field.

Example:

```julia
@mutt struct S
    x :: Int
    y
    S(x, y=x+1) = new(x,y)
end
```
