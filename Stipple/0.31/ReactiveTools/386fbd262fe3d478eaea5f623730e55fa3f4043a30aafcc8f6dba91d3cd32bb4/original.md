```julia
@in(expr)
```

Declares a reactive variable that is public and can be written to from the UI.

**Usage**

```julia
@app begin
    @in N = 0
end
```
