```
noautorun(handlers...)::Function
```

Constructs a wrapper function which can be used within @syntax_eff to skip all given handler types within the autorun.

## Example

```julia
@syntax_eff noautorun(Vector, Identity) begin
  a = [1,2,3]
  b = Identity(a + 2)
end
```

will actually run no handler at all in the implicit autorun, as both handlers are marked for ignore.
