```
WeakKeyIdDict([itr])
```

`WeakKeyIdDict()` constructs a hash table where the keys are weak references to objects which may be garbage collected even when referenced in a hash table.

See [`Dict`](https://docs.julialang.org/en/v1/base/collections/#Base.Dict) for further help. Note, unlike [`Dict`](https://docs.julialang.org/en/v1/base/collections/#Base.Dict), `WeakKeyIdDict` does not convert keys on insertion, as this would imply the key object was unreferenced anywhere before insertion.

See also [`WeakRef`](https://docs.julialang.org/en/v1/base/base/#Core.WeakRef), [`WeakKeyDict`](https://docs.julialang.org/en/v1/base/collections/#Base.WeakKeyDict).
