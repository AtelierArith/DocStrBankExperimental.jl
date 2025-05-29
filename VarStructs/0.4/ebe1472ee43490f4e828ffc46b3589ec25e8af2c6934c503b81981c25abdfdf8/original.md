```
Unset
```

The value of a VarStruct field when it is not set yet.

# Examples

```julia
mystruct = @var struct MyStruct
    x::Int64
end

typeof(mystruct.x) # Unset

```
