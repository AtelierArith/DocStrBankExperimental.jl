Used in the `@when` block:

```julia
@when (a, b) = x begin
    a + b
@otherwise
    0
end
```

See also: [`@when`](@ref)
