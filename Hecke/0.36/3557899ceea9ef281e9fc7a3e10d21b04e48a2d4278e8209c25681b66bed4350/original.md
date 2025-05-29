```
conductor(R::AlgAssAbsOrd, S::AlgAssAbsOrd, action::Symbol) -> AlgAssAbsOrdIdl
```

Returns the ideal $\{ x \in R \mid xS \subseteq R \}$ if `action == :right` and $\{ x \in R \mid Sx \subseteq R \}$ if `action == :left`. It is assumed that $R \subseteq S$.
