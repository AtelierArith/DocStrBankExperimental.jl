```
op1 ⊗ op2
```

tensor product for generic operators, alternative syntax: tensor(op1, op2)

# Examples

```
controlled(op) = Proj("Up") ⊗ Id + Proj("Dn") ⊗ op
Rxy(t) = exp(im * t * (X ⊗ X + Y ⊗ Y) / 4)
```
