```julia
@out(expr)
```

Declares a reactive variable that is public and readonly.

**Usage**

```julia
@app begin
    @out N = 0
end
```
