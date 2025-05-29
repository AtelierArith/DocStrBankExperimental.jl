```
@cc closure_expr
```

"Closure Check" is a macro that attempts to verify a closure is compatible with the borrow checker.

Only immutable references (created with `@ref` and `@bc`) are allowed to be captured; all other owned and borrowed variables that are captured will trigger an error.

# Examples

```julia
@own x = 1
@own :mut y = 2

@lifetime lt begin
    @ref ~lt z = x
    @ref ~lt :mut w = y
    
    # These error as the capturing breaks borrowing rules
    bad = @cc () -> x + 1
    bad2 = @cc () -> w + 1
    
    # However, you are allowed to capture immutable references
    good = @cc () -> z + 1
    # This will not error.
end
```
