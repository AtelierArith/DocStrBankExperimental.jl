```
preimage(f::ACSetTransformation,Y::StructACSet)
```

Inverse f (from A to B) as a map from subobjects of B to subobjects of A. Cast an ACSet to subobject, though this has a trivial answer when computing the preimage (it is necessarily the top subobject of A).
