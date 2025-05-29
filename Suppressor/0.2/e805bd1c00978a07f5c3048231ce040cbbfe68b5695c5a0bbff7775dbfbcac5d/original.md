```
@color_output enabled::Bool expr
```

Enable or disable color printing for the given expression. Often useful in combination with the `@capture_*` macros:

## Example

@color*output false begin     output = @capture*err begin         @warn "should get captured, not printed"     end end @test output == "WARNING: should get captured, not printed "
