```
@midic expr
```

Replaces all `Int`s in `expr` with a call to `midi(::Int)`. This allows the user to write integers where midi intervals are required. Does not work when `expr` contains integers that should not be converted or intervals that are not written as literal integers.
