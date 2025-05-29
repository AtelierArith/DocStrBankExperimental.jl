```
conductor(R::AlgAssAbsOrd, S::AlgAssAbsOrd, action::Symbol) -> AlgAssAbsOrdIdl
```

`action`が`:right`の場合は理想$\{ x \in R \mid xS \subseteq R \}$を返し、`action`が`:left`の場合は$\{ x \in R \mid Sx \subseteq R \}$を返します。$R \subseteq S$であると仮定します。
