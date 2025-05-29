```
FunctionBoundary <: Boundary
```

A boundary condition with a function that returns the phase factor for a given site. The boundary condition is encoded in form $ψ(x + R) = f(x)ψ(x)$, where $f(x)$ is the function and $R$ is the translation vector.

---

```
FunctionBoundary(f, translation)
```

Construct a `FunctionBoundary` with a given function and translation.

## Arguments

  * `f`: The function that returns the phase factor for a given site.
  * `translation`: The translation vector of the boundary representad as `AbstractTranslation`.   If an array is passed, it is converted to `Translation` automatically.
