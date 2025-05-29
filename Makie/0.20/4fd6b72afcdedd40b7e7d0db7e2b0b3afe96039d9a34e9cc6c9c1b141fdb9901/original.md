usage @extractvalue scene (a, b, c, d) will become:

```julia
begin
    a = to_value(scene[:a])
    b = to_value(scene[:b])
    c = to_value(scene[:c])
    (a, b, c)
end
```
