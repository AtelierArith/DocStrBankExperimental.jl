```
type Operator{T, N} <: ExprOp{T, N}
```

the type of base operators (like `X`, `Swap`, `C` ...), `T` is `Pure` or `Mixed` and `N` is an Int.

# Example

```
Operator("X")                      a base operator whose value is predefined by the sites
Operator("Z", [1 0 ; 0 -1])
Operator{Pure, 2}("Swap", [ 1 0 0 0 ; 0 0 1 0 ; 0 1 0 0 ; 0 0 0 1])
Operator("CX", controlled(X))
Operator("Sx", (Sp + Sm) / 2)
Operator("C", [0 1 ; 0 0], true)   a fermionic operator
```
