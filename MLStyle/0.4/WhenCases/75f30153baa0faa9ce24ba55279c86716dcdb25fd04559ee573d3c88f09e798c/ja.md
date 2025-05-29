`@when`ブロックで使用されます：

```julia
@when (a, b) = x begin
    a + b
@otherwise
    0
end
```

参照： [`@when`](@ref)
