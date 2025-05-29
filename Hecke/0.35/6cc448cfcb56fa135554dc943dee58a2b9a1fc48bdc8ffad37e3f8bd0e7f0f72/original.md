```
short_weierstrass_model(E::EllipticCurve{QQFieldElem}) ->
  (EE::EllipticCurve, EllCrvIso, EllCrvIso)
```

Transform a curve given in long Weierstrass form over QQ to short Weierstrass form. Return short form and both transformations for points on the curve; first transformation from E (long form) to EE (short form), second transformation is the inverse of this map.
