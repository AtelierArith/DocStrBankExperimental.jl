```
create_string_converter(add_show_method::Bool = true)
```

The HDF5.jl library (version 0.17.2) does not support `InlineStrings` or `StaticStrings` in structs. Standard `String`s are also not suitable for agent and edge types, as these must be bits types.

To address this limitation, `create_string_converter` generates gconversion methods between `String` and `SVector{N, UInt8}` instances (from the `StaticArrays` package).  Here, N represents the maximum number of bytes that can be stored, which for Unicode strings may exceed the character count due to variable-length encoding.

Instead of `SVector{N, UInt8}` also `VString{N}` can be used.

For example, you could create a Person struct with a fixed-size name field:

```julia
struct Foo
    foo::VString{20}
end
```

You can then construct a `Foo` instance using a regular string: `Foo("abc")`.

If `add_show_method` is set to `true` (the default), `show` methods are also defined for these `SVector`s. To avoid confusion while working with Julia's REPL, where the value might appear as a `String` while actually being an `SVector`, the output includes "(as UInt8-Vector)" after the value itself.

When `add_show_method` is set to `true` (which is the default behavior), `show` methods are automatically defined for the `SVector` types. To prevent potential confusion arising from the display of `SVector` values as `String`s, the output is formatted to include the annotation "::UInt8[]" following the value itself. 
