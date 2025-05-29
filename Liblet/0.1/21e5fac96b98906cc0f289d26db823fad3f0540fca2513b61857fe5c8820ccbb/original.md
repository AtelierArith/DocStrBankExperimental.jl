```
rightmost(d::Derivation, prod::AbstractArray{Production})::Derivation
```

Performs a *rightmost* derivation step. Applies the specified productions to the current rightmost nonterminal in the sentential form, one by one.
