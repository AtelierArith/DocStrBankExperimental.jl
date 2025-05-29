```
push_through_isogeny(f::Isogeny, v::RingElem) -> RingElem
```

$$
E \to E'
$$

を写像$f$とし、$S$を$v$の根である$x$座標を持つ$E$上の点の集合とします。写像$f$の核多項式が$v$を割り切ると仮定します。$f(S)$内の点$Q$の$x$座標が正確に根である多項式$\psi$を返します。
