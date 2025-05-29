```
residue_field(O::AbsSimpleNumFieldOrder, P::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, check::Bool = true) -> Field, Map
```

Returns the residue field of the prime ideal $P$ together with the projection map. If `check` is true, the ideal is checked for being prime.
