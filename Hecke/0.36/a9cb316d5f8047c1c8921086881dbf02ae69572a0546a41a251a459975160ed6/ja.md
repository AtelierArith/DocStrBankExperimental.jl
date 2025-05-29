```
push_through_isogeny(f::Isogeny, v::RingElem) -> RingElem
```

$$
E \to E'
$$

をイソジェニーとし、S を v の根である E 上の点の集合とします。f のカーネル多項式が v を割り切ると仮定します。$f(S)$ の点 $Q$ の x 座標が正確に根である多項式 psi を返します。
