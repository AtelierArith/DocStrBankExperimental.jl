```
infinitesimal(::TBAKind{:TBA}) -> 0
infinitesimal(::TBAKind{:BdG}) -> atol/5
infinitesimal(::Fermionic{:BdG}) -> 0
```

Infinitesimal used in the matrixization of a tight-binding approximation to be able to capture the Goldstone mode.
