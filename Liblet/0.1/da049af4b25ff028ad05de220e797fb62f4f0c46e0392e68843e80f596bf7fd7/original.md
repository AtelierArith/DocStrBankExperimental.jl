```
leftmost(d::Derivation, prod::AbstractArray{Production})::Derivation
```

Performs a *leftmost* derivation step. Applies the specified productions to the current leftmost nonterminal in the sentential form, one by one.
