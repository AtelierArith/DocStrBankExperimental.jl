```
is_torsion_unit(x::AbsSimpleNumFieldElem, checkisunit::Bool = false) -> Bool
```

Returns whether $x$ is a torsion unit, that is, whether there exists $n$ such that $x^n = 1$.

If `checkisunit` is `true`, it is first checked whether $x$ is a unit of the maximal order of the number field $x$ is lying in.
