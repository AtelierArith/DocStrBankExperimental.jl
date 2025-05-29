```
compose(op1::T, op2::T, modτ::Bool=true) where T<:SymOperation
```

Compose two symmetry operations `op1` $= \{W₁|w₁\}$ and `op2` $= \{W₂|w₂\}$ using the composition rule (in Seitz notation)

$\{W₁|w₁\}\{W₂|w₂\} = \{W₁W₂|w₁+W₁w₂\}$

By default, the translation part of the $\{W₁W₂|w₁+W₁w₂\}$ is reduced to the range $[0,1[$, i.e. computed modulo 1. This can be toggled off (or on) by the Boolean flag `modτ` (enabled, i.e. `true`, by default). Returns another `SymOperation`.

The multiplication operator `*` is overloaded for `SymOperation`s to call `compose`, in the manner `op1 * op2 = compose(op1, op2, modτ=true)`.
