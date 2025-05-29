```
@extract scene (a, b, c, d)
```

これは次のようになります

```julia
begin
    a = scene[:a]
    b = scene[:b]
    c = scene[:d]
    d = scene[:d]
    (a, b, c, d)
end
```
