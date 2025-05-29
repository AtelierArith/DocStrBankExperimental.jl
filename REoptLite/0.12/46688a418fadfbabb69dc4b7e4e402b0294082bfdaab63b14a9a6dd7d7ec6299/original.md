```
REoptInputs(fp::String)
```

Use `fp` to load in JSON scenario:

```
function REoptInputs(fp::String)
    s = Scenario(JSON.parsefile(fp))
    REoptInputs(s)
end
```

Useful if you want to manually modify REoptInputs before solving the model.
