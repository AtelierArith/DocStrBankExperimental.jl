```
@set_warn_order
```

Temporarily set the order threshold for warning about the ITensor order in a block of code.

# Examples

```julia
@set_warn_order 12 A * B

@set_warn_order 15 begin
  C = A * B
  E = C * D
end
```
