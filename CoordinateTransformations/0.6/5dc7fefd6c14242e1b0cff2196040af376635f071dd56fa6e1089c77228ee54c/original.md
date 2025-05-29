```
recenter(trans::Union{AbstractMatrix,Transformation}, origin::Union{AbstractVector, Tuple}) -> ctrans
```

Return a new transformation `ctrans` such that point `origin` serves as the origin-of-coordinates for `trans`. Translation by `±origin` occurs both before and after applying `trans`, so that if `trans` is linear we have

```
ctrans(origin) == origin
```

As a consequence, `recenter` only makes sense if the output space of `trans` is isomorphic with the input space.

For example, if `trans` is a rotation matrix, then `ctrans` rotates space around `origin`.
