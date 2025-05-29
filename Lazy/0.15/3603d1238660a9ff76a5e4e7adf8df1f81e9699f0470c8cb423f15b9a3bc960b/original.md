```
@as as, exs...
```

`@as` lets you name the threaded argmument

```
@as _ x f(_, y) g(z, _) == g(z, f(x, y))
```

All threading macros work over begin blocks

```julia
6 === @as x 2 begin
  x^2
  x+2
end
```
