```
@compose module Name
    [@mixin Parents, ...]
    ...
end
```

Creates a new composable module `Name`. Structs inside this module are merged with those of the same name in `Parents`.
