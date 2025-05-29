```
@extract scene (a, b, c, d)
```

This becomes

```julia
begin
    a = scene[:a]
    b = scene[:b]
    c = scene[:d]
    d = scene[:d]
    (a, b, c, d)
end
```
