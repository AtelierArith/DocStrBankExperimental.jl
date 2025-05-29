```
@config expr
```

Create a `Config` with a NamedTuple-like or block syntax.  The following examples create equivalent `Config`s:

```
@config (x.one=1, x.two=2, z=3)

@config x.one=1 x.two=2 z=3

@config begin
    x.one = 1
    x.two = 2
    z = 3
end

let
    c = Config()
    c.x.one = 1
    c.x.two = 2
    c.z = 3
end
```
