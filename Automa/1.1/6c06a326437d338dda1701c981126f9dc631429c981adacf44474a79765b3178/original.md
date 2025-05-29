```
generate_init_code([::CodeGenContext], machine::Machine)::Expr
```

Generate variable initialization code, initializing variables such as `p`, and `p_end`. The names of these variables are set by the `CodeGenContext`. If not passed, the context defaults to `DefaultCodeGenContext`

Prefer using the more generic `generate_code` over this function where possible. This function should be used if the initialized data should be modified before the execution code.

# Example

```julia
@eval function foo(data)
    $(generate_init_code(machine))
    p = 2 # maybe I want to start from position 2, not 1
    $(generate_exec_code(machine, actions))
    return cs
end
```

See also: [`generate_code`](@ref), [`generate_exec_code`](@ref)
