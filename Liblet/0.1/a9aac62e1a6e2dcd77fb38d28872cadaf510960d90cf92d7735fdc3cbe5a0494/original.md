```
leftmost(d::Derivation, prod::Production)::Derivation
```

Performs a *leftmost* derivation step. Applies the specified [`Production`](@ref) to the current leftmost nonterminal in the sentential form.
