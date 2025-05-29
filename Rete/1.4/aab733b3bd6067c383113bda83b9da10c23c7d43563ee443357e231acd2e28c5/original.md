```
HasSetOfInputsTrait(type)
```

A Rete node type with the HasSetOfInputsTrait stores its inputs as a set.

Any struct that is a subtype of AbstractReteNode with the field

```
    inputs::Set{AbstractReteNode}
```

will have this trait.
