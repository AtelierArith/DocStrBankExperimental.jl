```
PolymerSystem{T} <: AbstractSystem
```

The key of `χN_map` should be a two-element `Set`. Each element is the unique symbol for a specie. For example, the `χN_map` of an AB diblock copolymer is a `Dict` with one entry `Set([:A, :B]) => χN`.

Note: For Edwards Model A (homopolymer + implicit solvent), one has to add a dummy solvent component in the `components` array to make the function `multicomponent` return correct result.
