```
NotImplementedError(interface::String, method::String) <: Exception
```

Describes that a given method (in form of a `String` describing the signature) that's part of the given `interface` has not been implemented.

The given method should have the form `method(..., ::T, ...)`, where `...` are other arguments. The message displayed by this Exception refers to `T` directly, so there's no need to give any particular subtype here.

Compared to `MethodError`, a `NotImplementedError` communicates "there should be a method to call here, but it needs to be implemented by the developer making use of the interface". This is mostly used through the [`@required`](@ref) macro, which handles the message generation for you.

## Examples

Note how `MethodError` in the example below indicates that the method isn't intended to be called.

```jldoctest; filter = r"#unused#"
julia> using RequiredInterfaces: NotImplementedError

julia> abstract type Foo end

julia> bar(::Foo, ::Int) = throw(NotImplementedError("Foo", "bar(::T, ::Int)"))
bar (generic function with 1 method)

julia> struct Baz <: Foo end

julia> bar(Baz(), 1)
ERROR: NotImplementedError: The called method is part of a fallback definition for the `Foo` interface.
Please implement `bar(::T, ::Int)` for your type `T <: Foo`.
Stacktrace:
 [1] bar(::Baz, ::Int64)
   @ Main ./none:1
 [2] top-level scope
   @ none:1

julia> bar(1, Baz())
ERROR: MethodError: no method matching bar(::Int64, ::Baz)
The function `bar` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  bar(!Matched::Foo, !Matched::Int64)
   @ Main none:1

Stacktrace:
 [1] top-level scope
   @ none:1
```
