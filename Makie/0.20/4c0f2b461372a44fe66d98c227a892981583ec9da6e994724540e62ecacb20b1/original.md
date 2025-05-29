```
@get_attribute scene (a, b, c, d)
```

This will extract attribute `a`, `b`, `c`, `d` from `scene` and apply the correct attribute conversions + will extract the value if it's a signal. It will make those attributes available as variables and return them as a tuple. So the above is equal to: will become:

```julia
begin
    a = get_attribute(scene, :a)
    b = get_attribute(scene, :b)
    c = get_attribute(scene, :c)
    (a, b, c)
end
```
