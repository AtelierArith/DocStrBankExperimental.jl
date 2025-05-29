```julia
@private(expr)
```

Declares a non-reactive variable that cannot be accessed by UI code.

**Usage**

```julia
@app begin
    @private N = 0
end
```
