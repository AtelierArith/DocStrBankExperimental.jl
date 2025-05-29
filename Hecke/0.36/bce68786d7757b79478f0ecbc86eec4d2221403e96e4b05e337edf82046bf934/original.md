```
normal_form(T::TorQuadModule; partial=false) -> TorQuadModule, TorQuadModuleMap
```

Return the normal form `N` of the given torsion quadratic module `T` along with the projection `T -> N`.

Let `K` be the radical of the quadratic form of `T`. Then `N = T/K` is half-regular. Two half-regular torsion quadratic modules are isometric if and only if they have equal normal forms.
