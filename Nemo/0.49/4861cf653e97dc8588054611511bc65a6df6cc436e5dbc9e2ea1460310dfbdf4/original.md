```
lift(R::FqPolyRing, a::FqFieldElem) -> FqPolyRingElem
```

Given a polynomial ring over the base field of the parent of `a`, return a lift such that `parent(a)(lift(R, a)) == a` is `true`.
