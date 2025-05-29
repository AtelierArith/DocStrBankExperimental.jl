```
flat(G::FinGenAbGroup) -> FinGenAbGroupHom
```

与えられた群 $G$ が（反復）直積または（反復）テンソル積を使用して作成されている場合、フラット積への群同型を返します：$G := (A \oplus B) \oplus C$ の場合、同型 $G \to A \oplus B \oplus C$（または $\otimes$）を返します。
