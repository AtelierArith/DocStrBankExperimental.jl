isunset(x)

Returns true if the value of a field is not set yet.

# Examples

```julia
mystruct = @var struct MyStruct
    x::Int64
end

isunset(mystruct.x) # true
```

```julia
isunset( Unset() ) # true
```
