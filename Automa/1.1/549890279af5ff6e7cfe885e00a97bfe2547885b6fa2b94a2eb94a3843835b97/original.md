```
generate_exec_code([::CodeGenContext], machine::Machine, actions=nothing)::Expr
```

Generate machine execution code with actions. This code should be run after the machine has been initialized with `generate_init_code`. If not passed, the context defaults to `DefaultCodeGenContext`

Prefer using the more generic `generate_code` over this function where possible. This function should be used if the initialized data should be modified before the execution code.

# Examples

```
@eval function foo(data)
    $(generate_init_code(machine))
    p = 2 # maybe I want to start from position 2, not 1
    $(generate_exec_code(machine, actions))
    return cs
end
```

See also: [`generate_init_code`](@ref), [`generate_exec_code`](@ref)
