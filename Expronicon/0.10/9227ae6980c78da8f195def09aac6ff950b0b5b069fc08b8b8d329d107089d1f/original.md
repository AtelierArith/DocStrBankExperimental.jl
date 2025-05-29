```
@test_expr <type> <ex>
```

Test if the syntax type generates the same expression `ex`. Returns the corresponding syntax type instance. Requires `using Test` before using this macro.

# Example

```julia
def = @test_expr JLFunction function (x, y)
    return 2
end
@test is_kw_fn(def) == false
```
