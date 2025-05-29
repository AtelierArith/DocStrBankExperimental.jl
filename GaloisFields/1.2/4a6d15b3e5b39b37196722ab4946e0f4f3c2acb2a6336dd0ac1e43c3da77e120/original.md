```
const G = @GaloisField! 3 β^2 + 1
const G = @GaloisField! 𝔽₃ β^2 + 1
const G = @GaloisField! 3^2 β
const K = GaloisField(3)
const G = @GaloisField! K β^2 + 1
```

Define a finite field `G` and inject a variable for its primitive element into the current scope.

Note that the variable name (e.g. β above) is part of the type. This lets you define identifications between isomorphic (sub)fields. For example, with the following definition

```
const F = @GaloisField! 𝔽₂ β^2 + β + 1
const G = @GaloisField! 𝔽₂ γ^2 + γ + 1
```

the fields $F$ and $G$ are isomorphic, but not canonically. We might define

```
@GaloisFields.identify β => γ + 1
@GaloisFields.identify γ => β + 1
```

to allow for conversions like

```
G(β)
convert(F, γ + 1)
```
