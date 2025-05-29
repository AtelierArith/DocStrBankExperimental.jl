```
isexpr(x, ts...)
```

Convenient way to test the type of a Julia expression. Expression heads and types are supported, so for example you can call

```
isexpr(expr, String, :string)
```

to pick up on all string-like expressions.
