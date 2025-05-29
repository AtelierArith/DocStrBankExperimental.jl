```
@StenoGraph
```

The `@StenoGraph` macro allows you to refer to nodes without explicitly declaring them.

```jldoctest
@StenoGraph begin
    # a and b are not declared anywhere but they act as `Node(:a)` & `Node(:b)`
    a → b
end

# output

a → b
```

The main downside is that you can not use regular variables inside the macro. Had you declared `c = [Node(:a) Node(:b)]` outside the macro, inside it would nevertheless refer to `Node(:c)`. You would need to escape it using [`_`](@ref), i.e. use it as `_(c)` within the macro.

See also [`@declage_nodes`](@ref) & [`@declage_nodes_from`](@ref) for alternatives to escaping.
