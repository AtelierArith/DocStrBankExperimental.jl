```
evaluate(p::Union{ZZPolyRingElem, QQPolyRingElem}, f::TorQuadModuleMap)
                                                      -> TorQuadModuleMap
```

Given an abelian group endomorphism `f` of a torsion quadratic module `T` and an univariate polynomial `p` with integral coefficients, return the abelian group endomorphism $h := p(f)$ of `T` obtained by substituting the variable of `p` by `f`.

Note that one also simply call `p(f)` instead of writing `evaluate(p, f)`.
