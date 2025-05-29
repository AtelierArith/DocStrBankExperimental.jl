```
conductor(R::AlgAssAbsOrd, S::AlgAssAbsOrd, action::Symbol) -> AlgAssAbsOrdIdl
```

`action`が`:right`の場合、理想$\{ x \in R \mid xS \subseteq R \}$を返し、`action`が`:left`の場合、$\{ x \in R \mid Sx \subseteq R \}$を返します。$R \subseteq S$であると仮定します。
