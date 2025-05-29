```
codegen_match(f, x[, line::LineNumberNode=LineNumberNode(0), mod::Module=Main])
```

Generate a zero dependency match expression using MLStyle code generator, the syntax is identical to MLStyle.

!!! tip
    `codegen_match` is not available in ExproniconLite since it depends on MLStyle's pattern matching functionality.


# Example

```julia
codegen_match(:x) do
    quote
        1 => true
        2 => false
        _ => nothing
    end
end
```

This code generates the following corresponding MLStyle expression

```julia
@match x begin
    1 => true
    2 => false
    _ => nothing
end
```
