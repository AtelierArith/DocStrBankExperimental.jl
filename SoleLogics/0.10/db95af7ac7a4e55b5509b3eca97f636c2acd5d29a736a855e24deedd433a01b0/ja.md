```
(op::Operator)(o::Any)
```

`Operator`は構文トークン（例：原子）、構文木および/または数式を構成するために使用できます。

# 例

```julia-repl
    ¬(Atom(1)) ∨ Atom(1) ∧ ⊤
    ∧(⊤,⊤)
    ⊤()
```
