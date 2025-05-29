```
get_instruction_symbol(instruction::AbstractInstruction)::String
```

Returns the symbol string that is associated with an `instruction`.

# Examples

```jldoctest
julia> get_instruction_symbol(control_z(1, 2))
"cz"

```
