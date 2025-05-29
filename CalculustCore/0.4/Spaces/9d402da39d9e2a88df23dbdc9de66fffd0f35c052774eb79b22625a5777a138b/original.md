```
transformOp(V::AbstractSpace)
```

Get transform operator that takes vectors from `V` to `transform(V)`. To change transform operator to act on a different `AbstractVecOrMat` subtype, call

```
V = make_transform(V, input_prototype)
```
