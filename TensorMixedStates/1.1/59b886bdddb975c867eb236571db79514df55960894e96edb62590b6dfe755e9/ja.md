```
op1 ⊗ op2
```

一般的な演算子のテンソル積、代替構文: tensor(op1, op2)

# 例

```
controlled(op) = Proj("Up") ⊗ Id + Proj("Dn") ⊗ op
Rxy(t) = exp(im * t * (X ⊗ X + Y ⊗ Y) / 4)
```
