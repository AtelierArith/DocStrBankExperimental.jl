```
convert_value(T, x::Node[; upcast=false]) -> Node
```

Convert the values of node `x` to type `T`.

The value type of the resulting node is guaranteed to be `T` if and only if `upcast=true`. See further discussion in the note.

!!! note
    By default, `convert_value` has similar semantics to `Base.convert`, which means that the [`value_type`](@ref) of the returned node might be a subtype of `T`.

    A concrete example:

    ```jldoctest
    julia> x = convert_value(Any, constant("hello"));

    julia> value_type(x)
    String
    ```

    Note that the same thing would happen if calling `convert(Any, "hello")`.

    However, if we set `upcast=true`:

    ```jldoctest
    julia> x = convert_value(Any, constant("hello"); upcast=true);

    julia> value_type(x)
    Any
    ```

