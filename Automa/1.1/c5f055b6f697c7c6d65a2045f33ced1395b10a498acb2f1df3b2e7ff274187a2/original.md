```
generate_code([::CodeGenContext], machine::Machine, actions=nothing)::Expr
```

Generate init and exec code for `machine`. The default code generator function for creating functions, preferentially use this over generating init and exec code directly, due to its convenience.  Shorthand for producing the concatenated code of:

  * `generate_init_code(ctx, machine)`
  * `generate_action_code(ctx, machine, actions)`
  * `generate_input_error_code(ctx, machine)` [elided if actions == :debug]

# Examples

```
@eval function foo(data)
    # Initialize variables used in actions
    data_buffer = UInt8[]
    $(generate_code(machine, actions))
    return data_buffer
end
```

See also: [`generate_init_code`](@ref), [`generate_exec_code`](@ref)
