```
ionstate(object::Union{IonTrap, Chamber}, sublevels)
```

If `N = length(ions(object))`, returns N-dimensional ket corresponding to the ions being in the state $|sublevel₁⟩⊗|sublevel₂⟩⊗...⊗|sublevel\_N⟩$.

`sublevels` must be an length-`N` Vector, with each element specifying its corresponding ion's sublevel, using the same syntax as in `ionstate(ion::Ion, sublevel)`.
