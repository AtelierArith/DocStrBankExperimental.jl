```julia
@onchange(var, expr)
```

Declares a reactive update such that when a reactive variable changes `expr` is executed.

**Usage**

This macro watches a list of variables and defines a code block that is executed when the variables change.

```julia
@app begin
    # reactive variables taking their value from the UI
    @in N = 0
    @in M = 0
    @out result = 0
    # reactive code to be executed when N changes
    @onchange N, M begin
        result = 10*N*M
    end
end
```
