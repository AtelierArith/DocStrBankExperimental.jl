```
get_instruction_symbol(instruction::AbstractInstruction)::String
```

`instruction`に関連付けられたシンボル文字列を返します。

# 例

```jldoctest
julia> get_instruction_symbol(control_z(1, 2))
"cz"

```
