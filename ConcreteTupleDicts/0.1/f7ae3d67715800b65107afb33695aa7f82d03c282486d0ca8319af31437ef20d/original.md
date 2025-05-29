```
TupleDict(td)
TupleDict(d1, d2...)
```

Constructs a `TupleDict` from an iterable `td` of `Dict`s, or a sequence of `Dict`s `d1, d2, d3...`. 

`Dict`s which share a `valtype` are merged such that their keys are stored in the same `Dict`. `Dict`s     of distinct `valtype`s are left as separate `Dict`s in order to make `getkey` type inferrable.

Note that all input `Dict`s must satisfy the following constraints:

```
1. All `Dict`s must have concrete `keytype`, or a `keytype` which is a `Union{...}` of concrete types
2. You cannot pass in `Dict`s whose `keytype`s overlap
```

The first requirement helps us avoid amiguities where `Dict`s over abstract types may make identifying     the correct key ambiguous (e.g. two `Dict`s, one with `Number` and one with `Float64` keys).

The second requirement ensures/requires that all keys of a given type map to only one `valtype`.
