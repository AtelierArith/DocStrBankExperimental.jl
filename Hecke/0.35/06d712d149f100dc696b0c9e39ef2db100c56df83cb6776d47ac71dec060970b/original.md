```
flat(G::FinGenAbGroup) -> FinGenAbGroupHom
```

Given a group $G$ that is created using (iterated) direct products, or (iterated) tensor products, return a group isomorphism into a flat product: for $G := (A \oplus B) \oplus C$, it returns the isomorphism $G \to A \oplus B \oplus C$ (resp. $\otimes$).
